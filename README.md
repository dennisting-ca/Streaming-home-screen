# Streaming Home Screen
## Movie Recommender System Project

[Work In Progress]

### Note:
Due to size limitations of GitHub, the data, pickled models, and exported results are not included in this repository. 

### Project Goal:

The goal of this project is to create a movie streaming service’s home screen, with multiple sets of recommendations: 
- recommendations based on similar users
- recommendations based on popular movies
- recommendations based on a movie that the user has recently watched.

### Data:
MovieLens 25M Dataset from GroupLens Research (link: https://grouplens.org/datasets/movielens/)

### Part 1 - Exploratory Data Analysis (EDA) Highlights:
- Imported data and python libraries
- Inspected Data:
  - Checked for missing data / duplicate rows
  - Visualized Data (histograms, bar graphs, etc)
  - Grouped Data (value counts, etc)
- Data Manipulation:
  - Created 'net_ratings' - new feature calculated as <br />
    [(user rating on particular movie) - (average rating for this particular user)]
  - Merged (joined) datatables
  - Performed Train / Test split <br />
    [Note 1 - cross validation is performed in Grid Search, hence a validation set is not explicitly defined in this step] <br />
    [Note 2 - 'net_ratings' calculation for train data is not influenced by ratings in test set]
  - Filtered Data by dropping particular columns and rows by rationale explained in the Jupyter Notebook.
- Explored different metrics on how to define a "top movie"
- Exported relevant files for future notebooks


### Part 2 - Modelling Highlights:

- Exported relevant files for future notebooks
