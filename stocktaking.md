

```python
import pandas as pd
links = pd.read_csv('D:/sortedbysuraj5.0/data_analytics/DA project/ml-latest-small/links.csv')
movies= pd.read_csv('D:/sortedbysuraj5.0/data_analytics/DA project/ml-latest-small/movies.csv')
ratings = pd.read_csv('D:/sortedbysuraj5.0/data_analytics/DA project/ml-latest-small/ratings.csv')
tags = pd.read_csv('D:/sortedbysuraj5.0/data_analytics/DA project/ml-latest-small/tags.csv')

```


```python
print (links[0:5])
print("--------------------")
print("Number of unique movie-Ids")
links.T.apply(lambda x: x.nunique(), axis=1)[0]

```

       movieId  imdbId   tmdbId
    0        1  114709    862.0
    1        2  113497   8844.0
    2        3  113228  15602.0
    3        4  114885  31357.0
    4        5  113041  11862.0
    --------------------
    Number of unique movie-Ids
    




    9125




```python
print (movies[0:5])
movies.T.apply(lambda x: x.nunique(), axis=1)
print("--------------------")
print("list of genres\n")
print("Action,Adventure,Animation,Children's,Comedy,Crime,Documentary,Drama,Fantasy,Film-Noir,Horror,Musical,Mystery,Romance,Sci-Fi,Thriller,War,Western")
```

       movieId                               title  \
    0        1                    Toy Story (1995)   
    1        2                      Jumanji (1995)   
    2        3             Grumpier Old Men (1995)   
    3        4            Waiting to Exhale (1995)   
    4        5  Father of the Bride Part II (1995)   
    
                                            genres  
    0  Adventure|Animation|Children|Comedy|Fantasy  
    1                   Adventure|Children|Fantasy  
    2                               Comedy|Romance  
    3                         Comedy|Drama|Romance  
    4                                       Comedy  
    --------------------
    list of genres
    
    Action,Adventure,Animation,Children's,Comedy,Crime,Documentary,Drama,Fantasy,Film-Noir,Horror,Musical,Mystery,Romance,Sci-Fi,Thriller,War,Western
    


```python
print (ratings[0:5])
print("--------------------")
print("number of unique user-ids")
ratings.T.apply(lambda x: x.nunique(), axis=1)[0]

```

       userId  movieId  rating   timestamp
    0       1       31     2.5  1260759144
    1       1     1029     3.0  1260759179
    2       1     1061     3.0  1260759182
    3       1     1129     2.0  1260759185
    4       1     1172     4.0  1260759205
    --------------------
    number of unique user-ids
    




    671




```python
print (tags[0:5])

```

       userId  movieId                      tag   timestamp
    0      15      339  sandra 'boring' bullock  1138537770
    1      15     1955                  dentist  1193435061
    2      15     7478                 Cambodia  1170560997
    3      15    32892                  Russian  1170626366
    4      15    34162              forgettable  1141391765
    


```python

```
