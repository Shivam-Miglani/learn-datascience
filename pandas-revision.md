## Important concepts
* `DataFrame`: relational table with rows and *named* columns.
* `Series`: A single column. A `DataFrame` is made up of one or more `Series` and a name for each `Series`.
* `pd.Series([1,2,3,4,5,6])`
* `pd.DataFrame({'columnA': series1, 'columnB':series2, ...)`. This might fill some NAN values.
* `mydf = pd.read_csv('filename',sep=',',encoding='utf-8')`
* `mydf.describe()`: shows statistics about a Dataframe: count, mean, std, min, quantiles, max
* `mydf.head()`: shows fist few lines
* `mydf.hist('feature_name')`: shows a (histogram) distribution of values in a column.
### Access dataframe using Python dict/list operations: 
  * `mydf['c1'] #prints values of column called c1`
  * `mydf['c1'][1] #second value of column c1`
  * `type(mydf['c1'][1]) #type of second value in column c1`
  * `mydf[0:2] #first two rows of the DataFrame mydf`
  * `type(mydf[0:2]) #<class 'pandas.core.frame.DataFrame'>`
  * `mydf[0:15:2] #corresponds to [min: max+1: step]`
### Manipulating Data
