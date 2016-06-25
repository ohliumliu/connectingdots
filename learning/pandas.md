### General assumptions to keep in mind
  * DataSeries -> DataFrame -> 
  * DataFrame is indexed and each row corresponds to each index. `df.iloc(int)` or `df.loc(index_name)` for row accessing.
  * DataSeries is also indexed.
  * DataFrame dot or dictionary notation is for column access.
  
### Split-apply-combine pattern
  * Split: Oftentimes the df is a table, with two feature as index and column names. The purpose of split is to get something like 
           a relational database.
           
  ```python
  df_flat = df.stack().reset_index()
  df_flat.columns = [col-names]
  ```
  * Apply: Analyze the data based on a certain column. `group_by` is often used. The criteria could be as simple as col name
    or as complex as a function of all features. The returned value is a GroupBy object.
  
  * Combine: Apply aggregator methods on GroupBy objects (such as mean) to get statistics of each group. The result is a data frame. Another way to understand this: groupby results in the several datafames (groups) held together. In generate, one can call `apply(method)` on a groupby object to apply the given method to each frame. The method takes a dataframe as input, and return the result. This is similar to callback.
### Useful commands
  * query
  
  `df.query("col1 == 'OK' " & "col2 > 2")` or `df[df.col1 == "OK" and df.col2 > 2]`
  In the second case, the condition in the bracket returns a mask which is a data frame by itself.
  
  * sort
  
  `df.sort(col-name)`
  
  * assign
  
  ` df[col] = df.col1 + df[col2]` or `df.assign(new_col= col1*2, new_col2 = col1 + col2)`
  
  * delete column (drop column in SQL language)
  
  `del df[col]` or 
  `df.drop('lable', axis = 0) # default to drop a certain row, drop a col when axis = 1`
  
  * set index
  
  * merge
  `df1.merge(df2, left_on='id_from_df1', right_on='id_from_df2')` The duplicated col names will be renamed with suffix "_x" and "_y"
  Use `how` option to select inner, left, right or outer join.
  
  * read sql from database directly
  
  `df = pd.read_sql("SELECT ...", db)` Here `db` is a python db api object.
  
  * Python db api. Use SQLAlchemy for backends other than SQLite.
  ```python
  from sqlite3 import dbapi2 as sq3
  import os
  PATHSTART="."
  sqlite_db = sq3.connect(os.path.join(PATHSTART, dbfile))
  ```
  * view vs copy
     [Reference](http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy)

  ```python
  df.loc[labels, cols] # this returns a view of the dataframe. It can be used for both display and assignment. This is prefered.
  df[labels][cols] # this may or may not return a view. It's ok for display, but not safe for assignment.
  df.loc[labels][cols] # this returns a view. It's ok for display. It's NOT ok for assignment.
  ```
  The reason behind this is that the last two operations are two steps chained together. When used for assignment, the second operation
  may be operated on a copy of the first operation. In the first case, `.loc` can guarantee that operations are applied to `df` itself.
