#!/usr/bin/env python
# coding: utf-8

# In[66]:


import pandas as pd 
import numpy as np


# In[67]:


content=pd.read_csv("C:/Users/HP/Downloads/Content.csv")
reaction=pd.read_csv("C:/Users/HP/Downloads/Reactions.csv")
reactiontype=pd.read_csv("C:/Users/HP/Downloads/ReactionTypes.csv")
reactiontype


# In[68]:


content


# In[69]:


reaction


# In[70]:


mask=pd.DataFrame(reaction.merge(content,on='Content ID'))[['Content ID','Type','Datetime','Content Type','Category']]
mask


# In[71]:


filter=mask.merge(reactiontype,on='Type')[['Content ID','Type','Datetime','Content Type','Category','Sentiment','Score']]
filter


# In[72]:


#top five categories
top_five=pd.DataFrame(filter.groupby('Category')['Score'].sum().sort_values(ascending=False).head(5))
top_five


# In[73]:


filter.to_csv('clean_dataframe2.csv',index=False)


# In[74]:


#unique categories

unique_category=pd.DataFrame(filter['Category'].str.capitalize().unique(),columns=['categories'])
unique_category


# In[75]:


import pandas as pd
import matplotlib.pyplot as plt
from IPython.display import FileLink

# Data
labels = ['Studying', 'Healthy eating', 'Dogs', 'Public speaking', 'Science', 'Tennis', 'Food', 'Fitness', 'Soccer', 
          'Education', 'Travel', 'Veganism', 'Cooking', 'Technology', 'Animals', 'Culture']
sizes = [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]  # Each category has a count of 1

# Create DataFrame
data = {'Category': labels, 'Count': sizes}
df = pd.DataFrame(data)

# Save the DataFrame to CSV
df.to_csv('categories_distribution.csv', index=False)

# Plot
plt.figure(figsize=(10, 8))
colors = plt.cm.Paired(range(len(labels)))  # Use a colormap
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%', startangle=140)
plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.

# Title
plt.title('Categories Distribution')

# Show the plot
plt.show()

# Display a link to download the CSV file
FileLink('categories_distribution.csv')


# In[76]:


filter


# In[77]:


#Number of reactions vs category analysis 
reacts=pd.DataFrame(filter['Category'].value_counts().sort_values(ascending=False))
reacts.plot(kind='pie',y='count',subplots=True,figsize=(25,15),autopct='%0.1f%%',explode=[0.1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0])

plt.title('Number of reactions vs Category')

plt.show()
reacts.to_csv('Num_of_reactions VS category.csv', index=False)
FileLink('Num_of_reactions VS category.csv')


# In[78]:


#month with the most post which are posted
filter['Datetime']=pd.to_datetime(filter['Datetime'],format='%d-%m-%Y %H:%M')
filter['Month']=filter['Datetime'].dt.to_period('M')
months_counts=filter['Month'].value_counts()
fd=pd.DataFrame(months_counts)
fd.plot(kind='pie',y='count',subplots=True,figsize=(15,7),autopct='%0.1f%%',explode=[0.1,0.1,0,0,0,0,0,0,0,0,0,0,0])
plt.show()

fd.to_csv('month_with_most_posts.csv', index=False)
FileLink('month_with_most_posts.csv')


# In[79]:


#no.of post monthwise analysis
fd.plot(kind='bar',color='r',legend=False)
plt.title('post vs month analysis')
plt.xlabel('months')
plt.ylabel('number of posts')
plt.show()
fd.to_csv('month_with_most_num_of_posts.csv', index=False)
FileLink('month_with_most_num_of_posts.csv')


# In[80]:


# How does the average score change over time for each category?
month_avg=filter.set_index('Datetime').groupby('Category')['Score'].resample('M').mean().unstack()
month_avg.plot(kind='line',figsize=(12,6))
plt.title('Average Score Over Time by Category')
plt.xlabel('Date')
plt.ylabel('Average Score')
plt.legend(title='Category')
plt.show()

month_avg.to_csv('Average score over time by category.csv', index=False)
FileLink('Average score over time by category.csv')


# In[81]:


#How does the type of content impact the score across different categories?
import seaborn as sns
plt.figure(figsize=(14, 8))
sns.boxplot(x='Content Type', y='Score', hue='Category', data=filter)
plt.title('Score Distribution by Content Type and Category')
plt.xlabel('Content Type')
plt.ylabel('Score')
plt.legend(title='Category', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.show()





# In[82]:


top_five


# In[83]:


import matplotlib.pyplot as plt
colors=['red','green','orange','cyan','yellow']
top_five.plot(kind='bar',color=colors,figsize=(12,7))
plt.ylabel('scores')
plt.title('Top 5 Categories on basis of Score')

plt.show()


# In[84]:


#how do the reaction type vary across the top 5 categories
rc=df.merge(filter,how='inner',on='Category')


# In[85]:


type_cat=rc.groupby(['Category','Type']).size().unstack(fill_value=0)
type_cat


# In[86]:


type_cat.plot(kind='bar',figsize=(20,7))
plt.grid()
plt.title('Reaction Type ')


