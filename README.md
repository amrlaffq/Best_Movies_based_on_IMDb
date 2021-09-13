# Best Rated Movies Based on Netflix & IMDb
This project is about the best rated movies based on Netflix and IMDb
</p>
<img src="https://Python-pandas_Best_Movies_based_on_Netflix_IMDb/Movie images/netflix.jpg" alt="Figure"> 
</p>
<img src="https://Python-pandas_Best_Movies_based_on_Netflix_IMDb/Movie images/imdb.png" alt="Figure"> 

## Loading the dataset
The IMDb dataset were taken from two files:
```js
movies = pd.read_csv('archive/IMDb movies.csv')
rating = pd.read_csv('archive/IMDb ratings.csv')
```
After that, only attributes needed were merge together into a dataset.
```js
mov = movies.loc[:,['imdb_title_id','title','year','date_published','genre']]
rate = rating.loc[:,['imdb_title_id', 'total_votes', 'weighted_average_vote']]
imdb = mov.merge(how='outer', right=rate, right_on='imdb_title_id', left_on='imdb_title_id')
```
Later on, Netflix file was merge with the IMDb dataset:
```js
netflix = pd.read_csv('IMDB movies.csv/netflix_titles.csv')
net_imdb = imdb.merge(how= 'inner', right = netflix, right_on = ['title','release_year'], left_on = ['title','year'])
```

## By using Exploratory Data Analysis (EDA), data visualization were made from the collected dataset
Top 10 most popular genre
```js
import matplotlib as plt
genre_new = net_imdb.groupby('genre').size().to_frame('value').sort_values('value',ascending=False)
net_imdb.groupby('genre').size()
genre_new = sns.catplot(x="genre", y="value", kind="bar", data=genre_new).set_xticklabels(rotation=90)
```
</p>
<img src="https://Python-pandas_Best_Movies_based_on_Netflix_IMDb/Movie images/genre.PNG" alt="Figure"> 

Popular movies from each country
```js
pop_mov = high_rated_mov.groupby('country').size().to_frame('value').sort_values('value',ascending= False)
pop_mov = pop_mov.reset_index()
myFigure = sns.catplot(data=pop_mov, kind='bar', x='country', y='value')
myFigure.set_xticklabels(rotation=90)
```
</p>
<img src="https://Python-pandas_Best_Movies_based_on_Netflix_IMDb/Movie images/country.PNG" alt="Figure"> 
