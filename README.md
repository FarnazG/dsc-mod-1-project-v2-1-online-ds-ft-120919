# Module 1 Final Project Specifications

In this project, we will do some data analysis and presentation to explore what type of movies are currently doing the best at the box office and translate those findings into actionable insights that our client can use when deciding what type of movies they should produce.


## Dataset

For this project, we use some movie-related data from:

*Box Office Mojo
*IMDB
*Rotten Tomatoes
*TheMovieDB.org


## Insights

Q1: Categorize the top popular/profitable movies based on their genres.

Q2: Find the film-crew for the top profitable movies.

Q3: Categorize the top popular/profitable genres based on their investment budget.

Q4: Categorize the top popular/profitable genres based on their film crew.

Q5: With the available budget for our movie investment, what genre and what crew would be the best choice.


## Technical Aspect

To get to the question 5 which is the most practical result of our data analysis for our client, we need to answer all other questions by exploring our data sets, joining different tables and creating graphs.

1. In this project, Pandas DataFrame and matplotlib are **mainly** used for exploring and visualizing data.

2. We start with importing our available data:

#### Use glob to import all the csv files
```python
csv_files = glob("zippedData\\*.csv.gz")
```

3. Exploring data:

...Creating dataframe from each file.

```python
df(i) = pd.read_csv(csv_files[i])
```
...Getting basic information about each data frame.

#### Number of columns and rows,
```python
print(df(i).shape(), "\n\n")
```

#### Name of the columns,
```python
print(df(i).columns, "\n")
```

#### Values of the specific column:
```python
print(df(i)["specific column"].unique())
```

#### Total number of missing datas,type of objects and more information for each column:
```python
print(df(i).isna().sum(), "\n")
print(df(i).info, "\n")
print(df(i).describe(), "\n" )
```

4. We can employ different data manipulation methods to clean our dataframes/tables,

#### Drop columns:
```python
df(i)_clean = df(i).drop(["col1","col2","coli"],axis=1, inplace=False)
```

#### Drop rows:
```python
df(i)_clean = df(i).dropna(subset=["col1","col2"], how="any")
```

#### For sanity check, we measure how much data are missing for each column/row being dropped
```python
df(i).shape()
df(i)_clean.shape()
```

#### To replace or change the type of data:
```python
df(i)_replaced = df(i).col(i).str.replace("str1", "str2").astype(objecttype)
```

5. We create/join different dataframes to combine multiple data sets.

#### To create dataframe from pandas series:
```python
frame={"col1":series1 ,"col2":series2, "coli":seriesi}
df=pd.DataFrame(frame)
```
#### To merge different dataframes on matching values of specific column:
```python
df_merge = pd.merge(df1, df2, how='inner', on="col")
```

6. We finally create graphs to display the analysis outcomes,

![alt text](http://localhost:8888/view/Flatiron/finalprep/dsc-mod-1-project-v2-1-online-ds-ft-120919/graphs/image.png "scatter graph")


According to this plot, for low budget movies(up to $ 40000000) **drama** is the recommended choice of genre, while for the higher budget movies **action** is the best choice.

