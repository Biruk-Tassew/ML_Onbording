
Documentation: Analyzing IMDb Top 1000 Movies

This documentation provides a brief overview of how to analyze the IMDb Top 1000 movies dataset using pandas and matplotlib.


This code snippet is aimed at analyzing the IMDb Top 1000 movies dataset. It begins by importing the necessary libraries, namely pandas and matplotlib.pyplot. The dataset is then loaded using the pandas library, and the column names are extracted for further analysis. The average rating of the movies is calculated by taking the mean of the "IMDB_Rating" column. The code proceeds to explore the genres of the movies by splitting the "Genre" column and extracting unique genres. Finally, a histogram is generated to visualize the distribution of genres in the dataset.


```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("./imdb_top_1000.csv")

columns = df.columns.tolist()

average_rating = df["IMDB_Rating"].mean()
all_genres = df['Genre'].str.split(', ').explode()
unique_genre = all_genres.unique()
df
```




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
      <th>Poster_Link</th>
      <th>Series_Title</th>
      <th>Released_Year</th>
      <th>Certificate</th>
      <th>Runtime</th>
      <th>Genre</th>
      <th>IMDB_Rating</th>
      <th>Overview</th>
      <th>Meta_score</th>
      <th>Director</th>
      <th>Star1</th>
      <th>Star2</th>
      <th>Star3</th>
      <th>Star4</th>
      <th>No_of_Votes</th>
      <th>Gross</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://m.media-amazon.com/images/M/MV5BMDFkYT...</td>
      <td>The Shawshank Redemption</td>
      <td>1994</td>
      <td>A</td>
      <td>142 min</td>
      <td>Drama</td>
      <td>9.3</td>
      <td>Two imprisoned men bond over a number of years...</td>
      <td>80.0</td>
      <td>Frank Darabont</td>
      <td>Tim Robbins</td>
      <td>Morgan Freeman</td>
      <td>Bob Gunton</td>
      <td>William Sadler</td>
      <td>2343110</td>
      <td>28,341,469</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://m.media-amazon.com/images/M/MV5BM2MyNj...</td>
      <td>The Godfather</td>
      <td>1972</td>
      <td>A</td>
      <td>175 min</td>
      <td>Crime, Drama</td>
      <td>9.2</td>
      <td>An organized crime dynasty's aging patriarch t...</td>
      <td>100.0</td>
      <td>Francis Ford Coppola</td>
      <td>Marlon Brando</td>
      <td>Al Pacino</td>
      <td>James Caan</td>
      <td>Diane Keaton</td>
      <td>1620367</td>
      <td>134,966,411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://m.media-amazon.com/images/M/MV5BMTMxNT...</td>
      <td>The Dark Knight</td>
      <td>2008</td>
      <td>UA</td>
      <td>152 min</td>
      <td>Action, Crime, Drama</td>
      <td>9.0</td>
      <td>When the menace known as the Joker wreaks havo...</td>
      <td>84.0</td>
      <td>Christopher Nolan</td>
      <td>Christian Bale</td>
      <td>Heath Ledger</td>
      <td>Aaron Eckhart</td>
      <td>Michael Caine</td>
      <td>2303232</td>
      <td>534,858,444</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://m.media-amazon.com/images/M/MV5BMWMwMG...</td>
      <td>The Godfather: Part II</td>
      <td>1974</td>
      <td>A</td>
      <td>202 min</td>
      <td>Crime, Drama</td>
      <td>9.0</td>
      <td>The early life and career of Vito Corleone in ...</td>
      <td>90.0</td>
      <td>Francis Ford Coppola</td>
      <td>Al Pacino</td>
      <td>Robert De Niro</td>
      <td>Robert Duvall</td>
      <td>Diane Keaton</td>
      <td>1129952</td>
      <td>57,300,000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://m.media-amazon.com/images/M/MV5BMWU4N2...</td>
      <td>12 Angry Men</td>
      <td>1957</td>
      <td>U</td>
      <td>96 min</td>
      <td>Crime, Drama</td>
      <td>9.0</td>
      <td>A jury holdout attempts to prevent a miscarria...</td>
      <td>96.0</td>
      <td>Sidney Lumet</td>
      <td>Henry Fonda</td>
      <td>Lee J. Cobb</td>
      <td>Martin Balsam</td>
      <td>John Fiedler</td>
      <td>689845</td>
      <td>4,360,000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>https://m.media-amazon.com/images/M/MV5BNGEwMT...</td>
      <td>Breakfast at Tiffany's</td>
      <td>1961</td>
      <td>A</td>
      <td>115 min</td>
      <td>Comedy, Drama, Romance</td>
      <td>7.6</td>
      <td>A young New York socialite becomes interested ...</td>
      <td>76.0</td>
      <td>Blake Edwards</td>
      <td>Audrey Hepburn</td>
      <td>George Peppard</td>
      <td>Patricia Neal</td>
      <td>Buddy Ebsen</td>
      <td>166544</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>996</th>
      <td>https://m.media-amazon.com/images/M/MV5BODk3Yj...</td>
      <td>Giant</td>
      <td>1956</td>
      <td>G</td>
      <td>201 min</td>
      <td>Drama, Western</td>
      <td>7.6</td>
      <td>Sprawling epic covering the life of a Texas ca...</td>
      <td>84.0</td>
      <td>George Stevens</td>
      <td>Elizabeth Taylor</td>
      <td>Rock Hudson</td>
      <td>James Dean</td>
      <td>Carroll Baker</td>
      <td>34075</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>997</th>
      <td>https://m.media-amazon.com/images/M/MV5BM2U3Yz...</td>
      <td>From Here to Eternity</td>
      <td>1953</td>
      <td>Passed</td>
      <td>118 min</td>
      <td>Drama, Romance, War</td>
      <td>7.6</td>
      <td>In Hawaii in 1941, a private is cruelly punish...</td>
      <td>85.0</td>
      <td>Fred Zinnemann</td>
      <td>Burt Lancaster</td>
      <td>Montgomery Clift</td>
      <td>Deborah Kerr</td>
      <td>Donna Reed</td>
      <td>43374</td>
      <td>30,500,000</td>
    </tr>
    <tr>
      <th>998</th>
      <td>https://m.media-amazon.com/images/M/MV5BZTBmMj...</td>
      <td>Lifeboat</td>
      <td>1944</td>
      <td>NaN</td>
      <td>97 min</td>
      <td>Drama, War</td>
      <td>7.6</td>
      <td>Several survivors of a torpedoed merchant ship...</td>
      <td>78.0</td>
      <td>Alfred Hitchcock</td>
      <td>Tallulah Bankhead</td>
      <td>John Hodiak</td>
      <td>Walter Slezak</td>
      <td>William Bendix</td>
      <td>26471</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>999</th>
      <td>https://m.media-amazon.com/images/M/MV5BMTY5OD...</td>
      <td>The 39 Steps</td>
      <td>1935</td>
      <td>NaN</td>
      <td>86 min</td>
      <td>Crime, Mystery, Thriller</td>
      <td>7.6</td>
      <td>A man in London tries to help a counter-espion...</td>
      <td>93.0</td>
      <td>Alfred Hitchcock</td>
      <td>Robert Donat</td>
      <td>Madeleine Carroll</td>
      <td>Lucie Mannheim</td>
      <td>Godfrey Tearle</td>
      <td>51853</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 16 columns</p>
</div>




```python
genre_counts = all_genres.value_counts().reset_index()
genre_counts.columns = ['Genre', 'Count']
output_file = 'genre_counts.csv'
genre_counts.to_csv(output_file, index=False)
result = pd.read_csv("./genre_counts.csv")
result
```




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
      <th>Genre</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Drama</td>
      <td>724</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Comedy</td>
      <td>233</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Crime</td>
      <td>209</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adventure</td>
      <td>196</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Action</td>
      <td>189</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Thriller</td>
      <td>137</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Romance</td>
      <td>125</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Biography</td>
      <td>109</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Mystery</td>
      <td>99</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Animation</td>
      <td>82</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Sci-Fi</td>
      <td>67</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Fantasy</td>
      <td>66</td>
    </tr>
    <tr>
      <th>12</th>
      <td>History</td>
      <td>56</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Family</td>
      <td>56</td>
    </tr>
    <tr>
      <th>14</th>
      <td>War</td>
      <td>51</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Music</td>
      <td>35</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Horror</td>
      <td>32</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Western</td>
      <td>20</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Film-Noir</td>
      <td>19</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Sport</td>
      <td>19</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Musical</td>
      <td>17</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(12, 6))
plt.hist(all_genres, bins=len(unique_genre))

plt.xlabel('Genre')
plt.ylabel('Count')
plt.title('Number of Movies per Genre')
plt.xticks(rotation=45, ha='center')

plt.show()


```


![png](Tasks_files/Tasks_4_0.png)


The below code generates a scatter plot to visualize the number of movies released each year in the IMDb Top 1000 movies dataset. The plot shows the relationship between the years on the x-axis and the corresponding number of movies on the y-axis. The x-axis labels are rotated by 90 degrees for better readability.


```python
year_counts = df.groupby('Released_Year').size().reset_index(name='Series_Title')
years = year_counts['Released_Year']
movies = year_counts['Series_Title']

plt.scatter(years, movies)
plt.xlabel('Year')
plt.ylabel('Number of Movies')
plt.title('Number of Movies by Year')
plt.xticks(rotation=90, ha='center')

plt.show()
```


![png](Tasks_files/Tasks_6_0.png)




