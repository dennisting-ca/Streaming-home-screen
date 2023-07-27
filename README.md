# Streaming Home Screen
## Movie Recommender System Project

### Note:
Due to size limitations of GitHub, the data, pickled models, and exported results are not included in this repository. 

### Project Goal:

The goal of this project is to create a movie streaming service’s home screen, with multiple sets of recommendations: 
- recommendations based on similar users
- recommendations based on popular movies
- recommendations based on a movie that the user has recently watched

### Data:
MovieLens 25M Dataset from GroupLens Research (link: https://grouplens.org/datasets/movielens/)

### Part 1 - Exploratory Data Analysis (EDA) Highlights:
- Imported data and python libraries
- Inspected Data:
  - Checked for missing data / duplicate rows
  - Visualized Data (histograms, bar graphs, etc)
  - Grouped Data (value counts, etc)
- Data Manipulation:
  - Created `net_ratings` - new feature calculated as <br />
    [(user rating on particular movie) - (average rating for this particular user)]
  - Merged (joined) datatables
  - Performed Train / Test split <br />
    [Note 1 - cross validation is performed in Grid Search, hence a validation set is not explicitly defined in this step] <br />
    [Note 2 - `net_ratings` calculations for train data is not influenced by ratings in test set]
  - Filtered Data by dropping particular columns and rows by rationale explained in the Jupyter Notebook
- Explored different metrics on how to define a "top movie"
- Exported relevant files for future notebooks (csv, npz, etc)

### Part 2 - Modelling Highlights:
- Imported python libraries and relevant files exported from previous notebooks
- Inspection of data being loaded, to see if it's as expected
- Decided on metrics for Collaborative Filtering:
  - Fraction of Concordant Pairs (FCP)
  - Mean Absolute Error (MAE)  <br />
    [Equations, and discussion within Jupyter Notebook]
- *BaselineOnly* Model
  - Performed instantiating, fitting, testing of model
- *FunkSVD* Model
  - Performed Grid Search to fine tune the hyperparameters [with cross validation set at 3]:
    - `n_factors` – The number of factors. These are latent features (i.e. hidden features) related to users and movies
    - `n_epochs` – The number of iteration of the Stochastic Gradient Descent procedure (iterations to adjust factors to minimize error)
    - `lr_all` – The learning rate for all parameters. This is the parameter that controls how much to adjust the model in response <br />
  - Analyzed Grid Search results to obtain optimal hyperparameters
- *FunkSVD++* Model
  - Performed similar grid search as *FunkSVD* model above
  - *FunkSVD++* model takes into account 'implicit ratings' (i.e. the fact that a user rates an item is in itself an indication of preference)
- Compared FCP & MAE metrics of the 3 models above with each other (with visuals)
  - *FunkSVD++* model outperformed the models above, it appears that 'implicit ratings' helped it out-perform
- Vectorized movie tags with TF-IDF (Term Frequency - Inverse Document Frequency) and applied Cosine Similarity to its output to measure similarity between movies based on tags
- Pickled Models (i.e. "exported" trained models above) so that recommendations can be performed without having to retrain the model each time. Exported relevant files for future notebooks (csv, npz, etc)

### Part 3 - Recommendation Highlights:
- Imported python libraries and relevant files exported from previous notebooks
- Imported picked models from Models Jupyternotebooking (see Part 2 - Modelling Highlights above)
- Created Functions that would take 'user_id' as input, and provide movie recommendations (using pickled models / top movies / cosine similarity based on vectorized tags). 
