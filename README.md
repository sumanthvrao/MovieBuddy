Data Analytics Project for the year 2018

MovieBuddy
======

Isn't watching an entire movie all by yourself depressing? Watching any movie with like-minded  friends and loved ones helps you experience the joy of a comedy, the adventure of a thriller, the tears of drama , and a pinch of romance. We help you form your own clan of stormtroopers or your own school of wizards. In addition, we bring together users over a common screen in the prospects of helping them finding their partner at heart. We provide personalised movie recommendations from your own past viewing history and ensure your movie choices are unregrettable. Enjoy with your true MovieBuddy!

[Dataset Link](https://grouplens.org/datasets/movielens/100k/) (movielens-100k-dataset.zip)

[![Python 3](https://img.shields.io/badge/python-3-blue.svg)](https://www.python.org/download/releases/3.0/)
[![Jupyter notebook 3](https://img.shields.io/badge/jupyter%20notebook-5.0.0-orange.svg
)](https://jupyter-notebook.readthedocs.io/en/5.0.0/)


## Project Description

**MovieLens** offers dataset offers about 20 million ratings and 465,000 tag applications applied to 27,000 movies by 138,000 user.
Our aim is to bring together users with similar movie interests. In order to do this, we make use of users movie ratings and their information. We account for a variety of factors (location, interests , age .. to name some) before suggesting a MovieBuddy to you.<br>
Our data set contains: 
* 943 users , 1682 movies and 100000 ratings.
* Each user has rated at least 20 movies. 
* Simple demograpic information about Users.

## Overview
A brief gist of what each file in our repository stands for :<br>
* **BasicAnalysis_and_Stocktaking** - Basic summary statistics of the data. Visualizations capturing some key aspects of the data.
* **Getting_data_from_api** - tmdb id's were used to fetch additional data regarding movies from the website. tmdb API was used. Data of director, actor, actress, genre, etc were extracted and saved in the ml-100k folder.
* **ml-100k** - Complete Dataset from MovieLens together with the data extracted from the API's . This also contains the user-item matrix, predicted value matrix, obtained in later stages.
* **CF-surprise-all-algos.ipynb** - Comparison between algorithms for predicting rating. Surprise library was used. SVD, Cross_validation , Variations of KNN, were tried. SVD was chosen on the basis of RMSE.
* **CF_surprise_SVD.ipynb** - SVD Algorithm of Surprise was used to build predictions for those userid,movie id paris not in training dataset. top k items for each user were retained based on ratings.
* **Collaborative_filtering_RBM.ipynb** - Restricted Boltzman Machine approach for Collaborative Filtering. New, unwatched movies were suggested for a particular user in decresing order of likelihood.
* **Content_based_filtering.ipynb** - Generate content based suggestions based on combined probability of similar Director, Actors, Genre from other movies as features.
* **Final_Module.ipynb** - The final notebook containing the driver code and GUI to help get movie suggestions.
* **Front_End_Widget.ipynb** - Front_End_Widgets for Dynamic output. Download and compile to try the interactive output of the notebook.
* **JupyterLinks.md** - All .ipynb files have been hosted on nbviewer and their link posted here.
* **We_R_PYthons_LiteratureSurvey** - Litrature Survey for mid-term report.

Authors
------
* **Suraj Aralihalli** - [Profile](https://github.com/SurajAralihalli)<br>
* **Sumedh Pb** - [Profile](https://github.com/sumedhpb)<br>
* **Sumanth V Rao** - [Profile](https://github.com/sumanthvrao)<br>
