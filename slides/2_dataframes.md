# Data Frames

---

## Tabular Data

----

### DataFrame

- A __DataFrame__ (aka a table) is a 2-D labeled data structure with columns of potentially different types.
    - types: quantitative, qualitative (ordered, non-ordered, ...)
- First column is special: the __index__

![](dataframe.png)

----

### DataFrames are everywhere


<div class="container">

<div class="col">

- first goal of an econometrician: constitute a good dataframe
    - "cleaning the data"
- sometimes data comes from several linked dataframes
    - relational database
- dataframes / relational databases are so ubiquitous a language has been developed for them: SQL

</div>

<div class="col">

<img src="relational_database.png" width=50%>

</div>

</div>

---

## Pandas


```python
import pandas as pd
```

----

### pandas

- pandas = panel + datas
- created by WesMcKinsey, very optimized
- many options
- if in doubt: [minimally sufficient pandas](https://medium.com/dunder-data/minimally-sufficient-pandas-a8e67f2a2428)
    - small subset of pandas to do everything
- tons of online tutorials
    ex: [doc](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html)

----

### creating a dataframe (1)


```python
# from a dictionary
d = {
    "country": ["USA", "UK", "France"],
    "comics": [13, 10, 12]   
}
pd.DataFrame(d)
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
      <th>country</th>
      <th>comics</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USA</td>
      <td>13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>UK</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>France</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>

----

### creating a dataframe (2)


```python
# from a matrix
import numpy as np
M = np.array([
    [18, 150],
    [21, 200],
    [29, 1500]
])
    
df = pd.DataFrame( M, columns=["age", "travel"] )
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
      <th>age</th>
      <th>travel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18</td>
      <td>150</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>200</td>
    </tr>
    <tr>
      <th>2</th>
      <td>29</td>
      <td>1500</td>
    </tr>
  </tbody>
</table>
</div>

---

## File Formats

----

### Common file formats

- comma separated files: `csv` file
    - often distributed online
    - can be exported easily from Excel or LibreOffice
- stata files: use `pd.read_dta()`
- excel files: use `pd.read_excel()` or `xlsreader` if unlucky

----

### Comma separated file


```python
txt = """year,country,measure
2018,"france",950.0
2019,"france",960.0
2020,"france",1000.0
2018,"usa",2500.0
2019,"usa",2150.0
2020,"usa",2300.0
"""
open('dummy_file.csv','w').write(txt) # we write it to a file
```




    136




```python
df = pd.read_csv('dummy_file.csv') # what index should we use ?
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
      <th>year</th>
      <th>country</th>
      <th>measure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018</td>
      <td>france</td>
      <td>950.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>france</td>
      <td>960.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020</td>
      <td>france</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018</td>
      <td>usa</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>usa</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2020</td>
      <td>usa</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>

----

### "Annoying" Comma Separated File

- Sometimes, comma-separated files, are not quite comma-separated...
    - inspect the file with a text editor to see what it contains
    - add options to `pd.read_csv`


```python
txt = """year;country;measure
2018;"france";950.0
2019;"france";960.0
2020;"france";1000.0
2018;"usa";2500.0
2019;"usa";2150.0
2020;"usa";2300.0
"""
open('annoying_dummy_file.csv','w').write(txt) # we write it to a file
```




    136




```python
pd.read_csv("annoying_dummy_file.csv", sep=";")
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
      <th>year</th>
      <th>country</th>
      <th>measure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018</td>
      <td>france</td>
      <td>950.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>france</td>
      <td>960.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020</td>
      <td>france</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018</td>
      <td>usa</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>usa</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2020</td>
      <td>usa</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>

----

### Exporting a DataFrame

- pandas can export to many formats: `df.to_...`


```python
print( df.to_csv() )
```

    ,year,country,measure
    0,2018,france,950.0
    1,2019,france,960.0
    2,2020,france,1000.0
    3,2018,usa,2500.0
    4,2019,usa,2150.0
    5,2020,usa,2300.0
    



```python
df.to_stata('dummy_example.dta')
```

---

## Data Sources

----

### Types of Data Sources

- Where can we get data from ?
- Official websites
    - often in csv form
    - unpractical applications
    - sometimes unavoidable
    - open data trend: more unstructured data
- Data providers
    - supply an API (i.e. easy to use function)

<img src=bloomberg.png width=60%>

----

### Data providers

- commercial ones:
    - bloomberg, macrobond, factsets, quandl ...
- free ones:
    - `dbnomics`: many official time-series
    - `qeds`: databases used by quantecon
    - `vega-datasets`: distributed with altair
    - covid*: lots of datasets...
- reminder: python packages, can be installed in the notebook with
    - `!pip install ...`


```python
!pip install vega_datasets
```

----

```python
import vega_datasets
df = vega_datasets.data('iris')
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
      <th>sepalLength</th>
      <th>sepalWidth</th>
      <th>petalLength</th>
      <th>petalWidth</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>145</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.3</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>146</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>5.0</td>
      <td>1.9</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>147</th>
      <td>6.5</td>
      <td>3.0</td>
      <td>5.2</td>
      <td>2.0</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>148</th>
      <td>6.2</td>
      <td>3.4</td>
      <td>5.4</td>
      <td>2.3</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>149</th>
      <td>5.9</td>
      <td>3.0</td>
      <td>5.1</td>
      <td>1.8</td>
      <td>virginica</td>
    </tr>
  </tbody>
</table>
<p>150 rows × 5 columns</p>
</div>

----

### Inspecting data

- once the data is loaded as `df`, we want to look at some basic properties:
    - `df.head(5)` # 5 first lines
    - `df.tail(5)` # 5 first lines
    - `df.describe()` # summary
    - `df.mean()` # averages
    - `df.std()` # standard deviations


----

```python
df.head(2)
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
      <th>sepalLength</th>
      <th>sepalWidth</th>
      <th>petalLength</th>
      <th>petalWidth</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe()
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
      <th>sepalLength</th>
      <th>sepalWidth</th>
      <th>petalLength</th>
      <th>petalWidth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>150.000000</td>
      <td>150.000000</td>
      <td>150.000000</td>
      <td>150.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.843333</td>
      <td>3.057333</td>
      <td>3.758000</td>
      <td>1.199333</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.828066</td>
      <td>0.435866</td>
      <td>1.765298</td>
      <td>0.762238</td>
    </tr>
    <tr>
      <th>min</th>
      <td>4.300000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>0.100000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>5.100000</td>
      <td>2.800000</td>
      <td>1.600000</td>
      <td>0.300000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.800000</td>
      <td>3.000000</td>
      <td>4.350000</td>
      <td>1.300000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>6.400000</td>
      <td>3.300000</td>
      <td>5.100000</td>
      <td>1.800000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>7.900000</td>
      <td>4.400000</td>
      <td>6.900000</td>
      <td>2.500000</td>
    </tr>
  </tbody>
</table>
</div>



---

## Manipulating DataFrames

----

### Columns

- Columns are defined by attribute `df.columns`

```python
df.columns
```

    Index(['sepalLength', 'sepalWidth', 'petalLength', 'petalWidth', 'species'], dtype='object')



This attribute can be set


```python
df.columns = ['sLength', 'sWidth', 'pLength', 'pWidth', 'species']
df.head(2)
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
      <th>sLength</th>
      <th>sWidth</th>
      <th>pLength</th>
      <th>pWidth</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>

----

### Indexing a column

A column can be extracted using its name as in a dictionary (like `df['sLength']`)

```python
series = df['sWidth'] # note the resulting object: a series
series
```


    0      3.5
    1      3.0
    2      3.2
    3      3.1
    4      3.6
          ... 
    145    3.0
    146    2.5
    147    3.0
    148    3.4
    149    3.0
    Name: sWidth, Length: 150, dtype: float64




```python
series.plot()
```


    <AxesSubplot:>


    
![png](DataFrames_files/DataFrames_41_1.png)
    
----

### Creating a new column


```python
df['totalLength'] = df['pLength'] + df['sLength']
df.head(2)
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
      <th>sLength</th>
      <th>sWidth</th>
      <th>pLength</th>
      <th>pWidth</th>
      <th>species</th>
      <th>totalLength</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>6.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>6.3</td>
    </tr>
  </tbody>
</table>
</div>

----

### Replacing a column


```python
df['totalLength'] = df['pLength'] + df['sLength']*0.5
df.head(2)
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
      <th>sLength</th>
      <th>sWidth</th>
      <th>pLength</th>
      <th>pWidth</th>
      <th>species</th>
      <th>totalLength</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>3.95</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>3.85</td>
    </tr>
  </tbody>
</table>
</div>

----

### Selecting several columns

- Index with a list of column names


```python
e = df[ ['pLength', 'sLength'] ]
e.head(3)
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
      <th>pLength</th>
      <th>sLength</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.4</td>
      <td>5.1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.4</td>
      <td>4.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.3</td>
      <td>4.7</td>
    </tr>
  </tbody>
</table>
</div>

----

### Selecting lines (1)

- use index range


```python
df[2:4]
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
      <th>sLength</th>
      <th>sWidth</th>
      <th>pLength</th>
      <th>pWidth</th>
      <th>species</th>
      <th>totalLength</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>3.65</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
      <td>3.80</td>
    </tr>
  </tbody>
</table>
</div>

----

### Selecting lines (2)

- use boolean


```python
df['species'].unique()
```




    array(['setosa', 'versicolor', 'virginica'], dtype=object)




```python
bool_ind = df['species'] == 'virginica' # this is a boolean serie
```


```python
e = df[ bool_ind ]
e.head(4)
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
      <th>sLength</th>
      <th>sWidth</th>
      <th>pLength</th>
      <th>pWidth</th>
      <th>species</th>
      <th>totalLength</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>100</th>
      <td>6.3</td>
      <td>3.3</td>
      <td>6.0</td>
      <td>2.5</td>
      <td>virginica</td>
      <td>9.15</td>
    </tr>
    <tr>
      <th>101</th>
      <td>5.8</td>
      <td>2.7</td>
      <td>5.1</td>
      <td>1.9</td>
      <td>virginica</td>
      <td>8.00</td>
    </tr>
    <tr>
      <th>102</th>
      <td>7.1</td>
      <td>3.0</td>
      <td>5.9</td>
      <td>2.1</td>
      <td>virginica</td>
      <td>9.45</td>
    </tr>
    <tr>
      <th>103</th>
      <td>6.3</td>
      <td>2.9</td>
      <td>5.6</td>
      <td>1.8</td>
      <td>virginica</td>
      <td>8.75</td>
    </tr>
  </tbody>
</table>
</div>

----

### Selecting lines and columns

- sometimes, one wants finer control about which lines *and* columns to select:
    - use `df.loc[...]` which can be indexed as a matrix


```python
df.loc[0:4, 'species']
```




    0    setosa
    1    setosa
    2    setosa
    3    setosa
    4    setosa
    Name: species, dtype: object

----

### Combine everything


```python
# Let's change the way totalLength is computed, only for 'virginica'
index = (df['species']=='virginica')
df.loc[index,'totalLength'] = df.loc[index,'sLength'] + 1.5*df[index]['pLength']
```

    <ipython-input-57-c1b3e665535b>:4: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      df.loc[index]['totalLength'] = df.loc[index,'sLength'] + 1.5*df[index]['pLength']

---

## Reshaping DataFrames

----

The following code creates two example databases.

```python
txt_wide = """year,france,usa
2018,950.0,2500.0
2019,960.0,2150.0
2020,1000.0,2300.0
"""
open('dummy_file_wide.csv','w').write(txt_wide) # we write it to a file
```




    71




```python
txt_long = """year,country,measure
2018,"france",950.0
2019,"france",960.0
2020,"france",1000.0
2018,"usa",2500.0
2019,"usa",2150.0
2020,"usa",2300.0
"""
open('dummy_file_long.csv','w').write(txt_long) # we write it to a file
```




    136




```python
df_long = pd.read_csv("dummy_file_long.csv")
df_wide = pd.read_csv("dummy_file_wide.csv")
```

----

### Wide vs Long format (1)

- compare the following tables


```python
df_wide
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
      <th>year</th>
      <th>france</th>
      <th>usa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018</td>
      <td>950.0</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>960.0</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020</td>
      <td>1000.0</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_long
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
      <th>year</th>
      <th>country</th>
      <th>measure</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018</td>
      <td>france</td>
      <td>950.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>france</td>
      <td>960.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020</td>
      <td>france</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018</td>
      <td>usa</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>usa</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2020</td>
      <td>usa</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>

----

### Wide vs Long format (2)

- in long format: each line is an independent observation
    - two lines mayb belong to the same category (year, or country)
    - all values are given in the same column
    - their types/categories are given in another column
- in wide format: some observations are grouped
    - in the example it is grouped by year
    - values of different kinds are in different columns
    - the types/categories are stored as column names
- both representations are useful

----

### Converting from Wide to Long


```python
df_wide.melt(id_vars='year')
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
      <th>year</th>
      <th>variable</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018</td>
      <td>france</td>
      <td>950.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019</td>
      <td>france</td>
      <td>960.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020</td>
      <td>france</td>
      <td>1000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018</td>
      <td>usa</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>usa</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2020</td>
      <td>usa</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>

----

### Converting from Long to Wide


```python
df_ = df_long.pivot(index='year', columns='country')
df_
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="2" halign="left">measure</th>
    </tr>
    <tr>
      <th>country</th>
      <th>france</th>
      <th>usa</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018</th>
      <td>950.0</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>2019</th>
      <td>960.0</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>2020</th>
      <td>1000.0</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# the result of pivot has a "hierarchical index"
# let's change columns names
df_.columns = df_.columns.get_level_values(1)
df_
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
      <th>country</th>
      <th>france</th>
      <th>usa</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018</th>
      <td>950.0</td>
      <td>2500.0</td>
    </tr>
    <tr>
      <th>2019</th>
      <td>960.0</td>
      <td>2150.0</td>
    </tr>
    <tr>
      <th>2020</th>
      <td>1000.0</td>
      <td>2300.0</td>
    </tr>
  </tbody>
</table>
</div>

----

### groupby

`groupby` is a very powerful function which can be used to work directly on data in the long format.


```python
df_long.groupby("country").apply(lambda df: df.mean())
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
      <th>year</th>
      <th>measure</th>
    </tr>
    <tr>
      <th>country</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>france</th>
      <td>2019.0</td>
      <td>970.000000</td>
    </tr>
    <tr>
      <th>usa</th>
      <td>2019.0</td>
      <td>2316.666667</td>
    </tr>
  </tbody>
</table>
</div>

---

## Merging

----

### Merging two dataframes

- Suppose we have two dataframes, with related observations
- How can we construct one single database with all informations?
- Answer:
    - `concatenate` if long format
    - `merge` databases if wide format
- Lots of subtleties when data gets complicated
    - we'll see them in due time


```python
txt_long_1 = """year,country,measure
2018,"france",950.0
2019,"france",960.0
2020,"france",1000.0
2018,"usa",2500.0
2019,"usa",2150.0
2020,"usa",2300.0
"""
open("dummy_long_1.csv",'w').write(txt_long_1)
```




    136




```python
txt_long_2 = """year,country,recipient
2018,"france",maxime
2019,"france",mauricette
2020,"france",mathilde
2018,"usa",sherlock
2019,"usa",watson
2020,"usa",moriarty
"""
open("dummy_long_2.csv",'w').write(txt_long_2)
```




    150




```python
 """year,country,value,type
2018,"france",950.0,measure
2019,"france",960.0,measure
2020,"france",1000.0,measure
2018,"usa",2500.0,measure
2019,"usa",2150.0,measure
2020,"usa",2300.0,measure
2018,"france",maxime,type
2019,"france",mauricette,recipient
2020,"france",mathilde,recipient
2018,"usa",sherlock,recipient
2019,"usa",watson,recipient
2020,"usa",moriarty,recipient
"""
```
