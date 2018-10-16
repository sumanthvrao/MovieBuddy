
##nb viewer link of the file (better rendered):
* https://nbviewer.jupyter.org/github/sumanthvrao/We_R_Pythons/blob/master/stocktaking.ipynb
```python
import pandas as pd
import numpy as np
data = pd.read_csv('/media/sumanthvrao/Personal/PESU/SEMESTER 5/DA/PROJECT/We_R_Pythons/DataSet/data.csv')
item = pd.read_csv('/media/sumanthvrao/Personal/PESU/SEMESTER 5/DA/PROJECT/We_R_Pythons/DataSet/item.csv',encoding='windows-1252')
user = pd.read_csv('/media/sumanthvrao/Personal/PESU/SEMESTER 5/DA/PROJECT/We_R_Pythons/DataSet/user.csv')
genre = pd.read_csv('/media/sumanthvrao/Personal/PESU/SEMESTER 5/DA/PROJECT/We_R_Pythons/DataSet/genre.csv')
occupation = pd.read_csv('/media/sumanthvrao/Personal/PESU/SEMESTER 5/DA/PROJECT/We_R_Pythons/DataSet/occupation.csv')
```


```python
#number of unique users 
print(data.head())
print("----------------")
print(data.T.apply(lambda x:x.nunique(),axis=1)[0])
```

       user_id  item_id  rating  timestamp
    0      196      242       3  881250949
    1      186      302       3  891717742
    2       22      377       1  878887116
    3      244       51       2  880606923
    4      166      346       1  886397596
    ----------------
    943



```python
#Mimium number of ratings given by a user is 19
counts = data.groupby(['user_id']).agg(['count']).idxmin()[0]
print(counts)
```

    19



```python
#number of unique movies
print(item[1:2]) #information about a single movie
print(item.T.apply(lambda x:x.nunique(),axis=1)[0])
print("----------------")
#genre of movies
print(genre[1:]["genre"])
```

       movie_id       movie_title release_date  \
    1         2  GoldenEye (1995)    01-Jan-95   
    
                                      video_release_date  imdb_url  unknown  \
    1  http://us.imdb.com/M/title-exact?GoldenEye%20(...         0        1   
    
       Action  Adventure  Animation  Children's   ...     Fantasy  Film-Noir  \
    1       1          0          0           0   ...           0          0   
    
       Horror  Musical  Mystery  Romance  Sci-Fi  Thriller  War  Western  
    1       0        0        0        0       1       0.0  0.0      NaN  
    
    [1 rows x 24 columns]
    1682
    ----------------
    1          Action
    2       Adventure
    3       Animation
    4      Children's
    5          Comedy
    6           Crime
    7     Documentary
    8           Drama
    9         Fantasy
    10      Film-Noir
    11         Horror
    12        Musical
    13        Mystery
    14        Romance
    15         Sci-Fi
    16       Thriller
    17            War
    18        Western
    Name: genre, dtype: object



```python
#user information
print(user.T.apply(lambda x:x.nunique(),axis=1)[0]) #verified to be 943 across datasets
print("----------------")
print(user.head())
user.groupby(['gender']).agg(['count'])["user_id"]
#273 females and 670 males
```

    943
    ----------------
       user_id  age gender  occupation zip_code
    0        1   24      M  technician    85711
    1        2   53      F       other    94043
    2        3   23      M      writer    32067
    3        4   24      M  technician    43537
    4        5   33      F       other    15213





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
    </tr>
    <tr>
      <th>gender</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>273</td>
    </tr>
    <tr>
      <th>M</th>
      <td>670</td>
    </tr>
  </tbody>
</table>
</div>




```python
#mean age
np.mean(user["age"])
print("----------------")
#occupation of the users 
user.groupby(['occupation']).agg(['count'])["user_id"].sort_values('count',ascending=False)
#clearly most number of student users
```

    ----------------





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
    </tr>
    <tr>
      <th>occupation</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>student</th>
      <td>196</td>
    </tr>
    <tr>
      <th>other</th>
      <td>105</td>
    </tr>
    <tr>
      <th>educator</th>
      <td>95</td>
    </tr>
    <tr>
      <th>administrator</th>
      <td>79</td>
    </tr>
    <tr>
      <th>engineer</th>
      <td>67</td>
    </tr>
    <tr>
      <th>programmer</th>
      <td>66</td>
    </tr>
    <tr>
      <th>librarian</th>
      <td>51</td>
    </tr>
    <tr>
      <th>writer</th>
      <td>45</td>
    </tr>
    <tr>
      <th>executive</th>
      <td>32</td>
    </tr>
    <tr>
      <th>scientist</th>
      <td>31</td>
    </tr>
    <tr>
      <th>artist</th>
      <td>28</td>
    </tr>
    <tr>
      <th>technician</th>
      <td>27</td>
    </tr>
    <tr>
      <th>marketing</th>
      <td>26</td>
    </tr>
    <tr>
      <th>entertainment</th>
      <td>18</td>
    </tr>
    <tr>
      <th>healthcare</th>
      <td>16</td>
    </tr>
    <tr>
      <th>retired</th>
      <td>14</td>
    </tr>
    <tr>
      <th>lawyer</th>
      <td>12</td>
    </tr>
    <tr>
      <th>salesman</th>
      <td>12</td>
    </tr>
    <tr>
      <th>none</th>
      <td>9</td>
    </tr>
    <tr>
      <th>homemaker</th>
      <td>7</td>
    </tr>
    <tr>
      <th>doctor</th>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>


