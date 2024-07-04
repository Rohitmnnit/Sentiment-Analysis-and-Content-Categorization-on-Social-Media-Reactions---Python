
# Sentiment Analysis and Content Categorization on Social Media Reactions - Python

## Overview
The Sentiment Analysis and Content Categorization on Social Media Reactions - Python notebook analyzes and visualizes data related to social media interactions. It uses Python libraries for data analysis and visualization to explore various reaction types on social media platforms.

## Project Description
This notebook provides insights into social media interactions by categorizing content and analyzing different types of reactions. It includes data cleaning, preprocessing, analysis, and visualizations to help understand trends and patterns in social media reactions.

#### Key functionalities include:

Loading and exploring social media data.

Cleaning and preprocessing data.

Visualizing different reaction types using bar plots.

## Datasets
This project utilizes the following datasets:

#### ReactionTypes.csv
https://drive.google.com/file/d/1HjAXHYC1JaX7q2wXgXXLzmpioIKD2pBu/view?usp=drive_link

Contains information about different reaction types, their sentiment, and associated score.

#### Columns:

Unnamed: 0: Index column

Type: The type of reaction (e.g., heart, want, disgust, hate, interested)

Sentiment: Sentiment of the reaction (e.g., positive, negative)

Score: Score associated with the reaction

#### Content.csv
https://drive.google.com/file/d/1QDcZ0hlZCaZkWVrIIIOmvzlxZ-oW-v4n/view?usp=sharing

Contains information about different content items, their type, and category.

#### Columns:
Unnamed: 0: Index column

Content ID: Unique identifier for the content

Content Type: Type of content (e.g., photo, video)

Category: Category of the content (e.g., studying, healthy eating, technology, food)

#### Reactions.csv
https://drive.google.com/file/d/1asi2lb1TmzNWHBWka6Jvxnfv-vO1Mrpf/view?usp=drive_link

Contains records of reactions to different content items, including the type of reaction and the datetime it occurred.

#### Columns:

Unnamed: 0: Index column

Content ID: Unique identifier for the content

Type: The type of reaction (e.g., disgust, dislike, scared, interested)

Datetime: The datetime when the reaction occurred (e.g., 07-11-2020 09:43)

## Installation
To run this notebook, you need Python installed on your system. Follow the steps below to set up the environment:

### Clone the repository:
https://github.com/Rohitmnnit/Sentiment-Analysis-and-Content-Categorization-on-Social-Media-Reactions---Python/tree/main
### Install the required packages:
    pip install -r requirements.txt


## Usage
To use this notebook:

### Open the Jupyter Notebook:
https://github.com/Rohitmnnit/Sentiment-Analysis-and-Content-Categorization-on-Social-Media-Reactions---Python/blob/main/socialbuzzForageProject.ipynb

Run the cells sequentially to perform data analysis and visualization.

## Dependencies
The project requires the following Python packages:

pandas

matplotlib

numpy

seaborn

You can install these using pip:

    pip install pandas matplotlib numpy seaborn


## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any bug fixes, features, or enhancements.

Fork the repository.

Create a new branch.

Commit your changes.

Push to the branch.

Open a pull request.
