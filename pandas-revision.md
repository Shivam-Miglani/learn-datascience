### Important concepts
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
* Can apply Python's basic operations to a Series. `series1/1000`
* Pandas `Series` can be used as arguments to most NumPy functions. E.g. `np.log(population)`, here population is name of the `Series`.
* `Series.apply`: `population.apply(lambda val: val > 1000000)`. It is used like Python's `map` function and the argument is a `lambda function`.
* Modifying `DataFrames` is straightforward. Just assign new `Series` to `mydf['c2']`.
* `cities['Population density'] = cities['Population'] / cities['Area square miles']
* Use bitwise `&` to take and of two Series.
### Indexes
* Indexes is a property defined by `Series` and `DataFrame` objects. 
* It does not change on data reordering as they signify original ordering of the source data.
* `mydf.reindex([2,0,1]) # list of indexes to manually reorder the indexes.`

### Shuffle the data
Indexes provide a great way to shuffle(randomize) a `DataFrame`. 
`cities.reindex(np.random.permutation(cities.index)) #shuffles values in-place. Also shuffles the rows`

* `reindex` allows index values that are not in original `DataFrame`'s index values and fills them with NaN. This is allowed because indexes are often strings pulled from the actual data. It then makes reindexing using an external list easy.




