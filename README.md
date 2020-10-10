Link to Report - https://github.com/sumanthvrao/We_R_Pythons/blob/master/We_R_Pythons_FinalReport.pdf

MovieBuddy
======

How  amazing would it be if you could watch your favorite movie with someone who has similar interests like you! Our model not only recommends you a movie you would love to watch but also brings together people with similar preference in movies. We have tried 3 different recommendation techniques to empower this idea.

[Dataset Link](https://grouplens.org/datasets/movielens/100k/) (movielens-100k-dataset.zip)

[![Python 3](https://img.shields.io/badge/python-3-blue.svg)](https://www.python.org/download/releases/3.0/)
[![Jupyter notebook 3](https://img.shields.io/badge/jupyter%20notebook-5.0.0-orange.svg
)](https://jupyter-notebook.readthedocs.io/en/5.0.0/)
[![Collaborative filtering](https://img.shields.io/badge/collaborative-filtering-red.svg
)](#)
[![Content Based filtering](https://img.shields.io/badge/contest%20based-filtering-yellow.svg)](#)
[![Surprise Library](https://img.shields.io/badge/surprise-library-brightgreen.svg)](http://surpriselib.com/)
[![TensorFlow](https://img.shields.io/badge/tensorflow%20-1.5-blue.svg)](http://surpriselib.com/)

## Project Description

**MovieLens** offers dataset offers about 20 million ratings and 465,000 tag applications applied to 27,000 movies by 138,000 user.
Our aim is to bring together users with similar movie interests. In order to do this, we make use of users movie ratings and their information. We account for a variety of factors (location, interests , age .. to name some) before suggesting a MovieBuddy to you.<br>
Our data set contains: 
* 943 users , 1682 movies and 100000 ratings.
* Each user has rated at least 20 movies. 
* Simple demograpic information about Users.

### Approach 1 - Content Based Filtering

Content based filtering also referred to as cognitive filtering recommends items based on comparison between the content of items which means the items recommended by the model is same for any user. Content-based filtering avoids the cold-start problem that forestalls other recommendation techniques, as the the system considers only the content of the movies to make recommendations.

Content Based Recommendations rely on the characteristics of the item itself. The major challenge is in identifying these characteristics of the item to be considered. The Original MovieLens dataset consists of limited information about each movie - details like movie title, year of release, movie id, imdb url and list of genres. This data alone was insufficient to bring out valuable recommendations for a movie. We used tmdb (The Movie Database) api to extract more details for each movie. This api enabled us to obtain other characteristics like names of the protagonists, director etc. We created a hybrid feature for each movie which comprised of the name of the movie, year of release, list of genres, name of the director, name of the primary actor, name of secondary actor.

The Countvectorizer module identified 9105 distinct new features for each movie where each feature is a word extracted from the hybrid feature set of all the movies. We then calculated the self-cosine similarity of the matrix to compare each movie with every other movie in the dataset. Based on this similarity matrix we recommend 15 movies for every given movie.

### Approach 2 - Collaborative Filtering

Collaborative filtering is a method of making automatic predictions (filtering) about the interests of a user by collecting preferences from many users. The collaborative filtering model attempts to recommend movies and how much a user likes each movie by considering either user-user similarity or movie-movie similarity

Surprise (Simple Python RecommendatIon System Engine) library was used for Collaborative filtering. Results of running different collaborative filtering algorithms have been documented in the table below.

| Algorithm                         | Mean RMSE | Mean MAE | Mean fit time | Mean test time |
|-----------------------------------|-----------|----------|---------------|----------------|
| SVD                               | 0.9358    | 0.7375   | 11.38         | 0.45           |
| KNN Basic (pearson baseline)      | 1.0005    | 0.7917   | 5.65          | 10.91          |
| KNN Basic (MSD)                   | 0.979     | 0.7731   | 1.23          | 8.47           |
| KNN Basic (cosine)                | 1.0174    | 0.8045   | 4.41          | 9.26           |
| KNN with means (pearson baseline) | 0.9382    | 0.731    | 4.5           | 8.74           |
| KNN with means (MSD)              | 0.9502    | 0.7486   | 1.34          | 9.71           |
| KNN with means (cosine)           | 0.9556    | 0.7546   | 4             | 8.55           |

We chose SVD as our collaborative filtering algorithm as it had the least testing time, and lower RMSE and MAE values across the 5-folds.

### Approach 3 - Restricted Boltzman Machine

The fundamental idea here is to use an RBM for each user with shared weights for users who rate the same set of movies. Every RBM has the same number of hidden units, but an RBM has active softmax visible units only for the items rated by that user. If two users have rated the same movie, their two RBM’s must use the same weights between the softmax unit for that movie and the hidden units. To ensure binary mappings, nodes with ratings from 1 to k are made for every user’s RBM for each movie he/she has rated. Each node is activated or deactivated based on the value it is looking for. It is shown that an RBM slightly outperform carefully tuned SVD models. A 2 layered undirected neural network was used as an RBM in our case.

## File Structure
A brief gist of what each file in our repository stands for :<br>
* **BasicAnalysis_and_Stocktaking** - Basic summary statistics of the data. Visualizations capturing some key aspects of the data.
* **Getting_data_from_api** - Fetching additional tmdb data
* **ml-100k** - Complete Dataset from MovieLens together with the data extracted from the API's . This also contains the user-item matrix, predicted value matrix, obtained in later stages.
* **CF-surprise-all-algos.ipynb** - Comparison between algorithms for predicting rating.
* **CF_surprise_SVD.ipynb** - SVD Algorithm of Surprise was used to build predictions for those user id - movie id pairs not in training dataset. Top k items for each user were retained based on ratings.
* **Collaborative_filtering_RBM.ipynb** - Restricted Boltzman Machine approach for Collaborative Filtering. New, unwatched movies were suggested for a particular user in decresing order of likelihood.
* **Content_based_filtering.ipynb** - Generate content based suggestions based on combined probability of similar Director, Actors, Genre from other movies as features.
* **Final_Module.ipynb** - The final notebook containing the driver code and GUI to help get movie suggestions.
* **Front_End_Widget.ipynb** - Front_End_Widgets for Dynamic output. Download and compile to try the interactive output of the notebook.
* **JupyterLinks.md** - All .ipynb files have been hosted on nbviewer and their link posted here.


Authors
------
* **Suraj Aralihalli** - [Profile](https://github.com/SurajAralihalli)<br>
* **Sumedh Pb** - [Profile](https://github.com/sumedhpb)<br>
* **Sumanth V Rao** - [Profile](https://github.com/sumanthvrao)<br>
