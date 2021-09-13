# Best Rated Movies Based on Netflix & IMDb
This project is about the best rated movies based on Netflix and IMDb
</p>
<img src="https://Python-pandas_Best_Movies_based_on_IMDb/Movie images/netflix.jpg" alt="Figure"> 
</p>
<img src="https://Python-pandas_Best_Movies_based_on_IMDb/Movie images/imdb.png" alt="Figure"> 

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
</p>
<img src="https://Python-pandas_Best_Movies_based_on_IMDb/Movie images/country.PNG" alt="Figure"> 
</p>
<img src="https://Python-pandas_Best_Movies_based_on_IMDb/Movie images/genre.PNG" alt="Figure"> 
