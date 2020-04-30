---
title: Data Manipulation using Pandas and Scikit-learn
linktitle: Data Manipulation using Pandas and Scikit-learn
toc: true
type: docs
date: "2020-04-29T00:00:00+01:00"
draft: false
menu:
  resources:
    parent: Resources
    name: Data Manipulation using Pandas and Scikit-learn
    weight: 10

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## General

Many methods have an `inplace` argument which performs the operation inplace when set to `True` so that you do not need to overwrite the original `DataFrame`. It produces cleaner code as well as saves time and memory! Note that method chaining does not work with `inplace=True` since nothing is returned.

Rows and columns behave in the exact same way. Indeed, they are both implemented using `pandas.Index` or `pandas.MultiIndex` objects. The main difference is that columns can be indexed in an additional way since `pandas.DataFrame` objects can be access through the native `python` indexing, i.e., `df[column]`. Otherwise, most (all?) operations can be perform along any of the two axes. (If not, there is the `.T` or `.transpose()` methods to flip the `DataFrame`.)

## Data Importation

You probably all know about `pandas.read_csv` to load text files into `pandas` `DataFrame`s. Here are some interesting options you might not know about:

- You can overwrite the column names directly using `names=[...]` and `header=0`;
- You can set the `index` automatically using `index_col="column_name"`;
- You can drop columns or rows before loading using `usecols=[...]` or `skiprows=[...]`, respectively;
- If `NA`s are encoded in a particular way, you can specify it using `na_values=[...]`;
- `encoding` might be useful to fix some problems related to encoding;
- `delim_whitespace` can be useful when the separator is a variable number of whitespaces instead of a given character (`,`, `\t`, etc.);

Most of these operations can be done in separate steps after loading(for example, you could do a `.replace(..., inplace=True)` to change some values to `NaN`), but it might be better to do them in one step to improve legibility, speed and memory consumption.

## Data Exportation
You are probably aware of the `.to_csv` method to write a `pandas` `DataFrame` to a text file. Here are some interesting options:

- `na_rep` to encode `NA`s in a particular way;
- `columns` to only write specific columns;
- `index`, `index_label` and `header` to control the output.

TODO: to_latex, apply(.format)

## Accessing Values

There are multiple ways to access the contents in a `pandas` `DataFrame` (most also work for `Series` as well).

Using `python` indexing (a `DataFrame` behaves as a dictionary of columns):
- `df[columns]`: return all columns in `columns`;
    - `columns` can be string (one column is returned) or a list of string.

Using `.loc`:
- `df.loc[index_values]`: returns the rows corresponding to `index_values`;
    - `index_values` can be a single index value, a list of index values, a slice of values `startrow:endrow` or even a Boolean of the same length as `df`;
- `df.loc[index_values, columns]`: returns the specified columns of the specified rows;
- `df.loc[:, columns]`: does the same as `df[columns]`;
- `df.loc[index_values, :]`: does the same as `df.loc[index_values]`.

Using `.iloc`:
- `df.iloc[index]`: return the rows corresponding to `index` using integer indexing;
    - `index` can be a single integer, a list of integers or even a range of integer `startnum:endnum`;
- `df.iloc[row_index, col_index]`: returns the specified rows and columns.

Using `.at` to access a single value:
- similar indexing as `.loc`.

Using `.iat`:
- similar indexing as `.iloc`.

Using `.query()` can be used to select rows on some truth value defined by a string statement similar to that of SQL.

Here are some interesting methods to create Boolean arrays to use in `.loc[]`:
- `.isna()`, `.notna()` checks whether values are `NaN`;
- `.isin()` corresponds to elementwise native `in`;
- `.le`, `.lt`, `.ge`, `.gt`, `.eq` and `.ne` are equivalent to `<=`, `<`, `>=`, `>`, `==` and `!=`, respectively;
- `.between_time()` when dealing with `datetime` format;
- Any `Series` methods:
    - `.between()` is a nice shorthand for two comparisons;
    - `.str.<method>` when dealing with strings
    - `.dt.<method>` when dealing with datetime formats
    - `.cat.<method>` when dealing with categorical values

## Setting Values

To set values in a existing `DataFrame`, you can use all previous indexing methods:
- Use `df[columns]` or `df.loc[:, columns]` or `df.iloc[:, columns]` to set or add columns;
- Use `df.loc[index]` or `df.loc[index, :]` or `df.iloc[index, :]` to set or add rows;
- Use `df.loc[index, columns]` or `df.iloc[index, columns]` to set specific entries:    
- same with `.at` and `.iat` to fill a specific cell.

Note that new rows and columns might be added if `index` or `columns` contains values not in the current `df`. The `.iloc` and `iat` indexing generally does not support adding new rows and columns and raises an out-of-bound error when trying to set values outside the current `df`.

For any of these methods the syntax is through assignment where the right-hand side can be various things:
- a list of list (e.g. a `numpy` array),
- a dict `column: values`,
- a single value copied for all cells,
- a `pandas` `Series` or `Dataframe` object,
- and many more combinations!

To add new rows to a `DataFrame`, you can use one of the following:
- `df.loc[index] = row`
- merging two `DataFrame`s with same columns (see [Merging DataFrames](#merging))

To add new columns:
- Use `df[columns] = values` (multiple columns)
- Use `df.insert(loc, column, values)` (single column)
- merging two `DataFrame`s with same indices (see [Merging DataFrames](#merging))

Other interesting methods:
- The `df.where()` method can also be used to replace values where some condition is false;
- The `df.mask()` method is the converse to `.where`: it replaces values where the condition is true;
- The `df.replace()` replaces values;
- The `df.filter()` method can select some rows/columns based on their content (`like` or a `regex`).
- Using `df.take()` performs similarly as `.iloc[]`;
- Using `df.fillna()` does what its name indicates;
- The `df.update(other_df)` can be useful in some cases (see [Merging DataFrames](#merging) for more details);
- The `df.eval(str, inplace=True)` method lets you compute a new column using a string description;

## Subsetting Data

Subsetting data can be viewed in two ways: selecting rows/columns or dropping rows/data.

To select rows or columns, refer to [Accessing data](#access). 

To drop rows or columns, you can:
- Select your subset and overwrite the `DataFrame` as in `df = df.loc[...]`;
- Use the `df.drop(..., inplace=True)` method to drop rows or columns;

For more specific use cases:
- Use `df.drop_duplicates(..., inplace=True)` to drop repeated rows
- Use `df.dropna(..., inplace=True)` to drop rows or columns if they contain `NaN` values.
- Use `df.truncate()` when the condition is a range of indices.

## Reshaping DataFrames

Transpose:
- The method s `.T` and `.transpose()` do the same thing

## Wide to long format
- The method `df.melt()`: take multiple columns into (column name, value);
- The method `df.stack()`: similar to melt, but less general; puts the original column names into a `MultiIndex` rather than new columns;
- The method `df.explode()`: when cells contains lists, this methods expand the dataframe for each element of the list.


```python
import pandas as pd
df_wide = pd.DataFrame({"A": range(5), "B": range(5, 10), "C": range(10, 15)}, index=list("abcde"))
print(df_wide)
```

       A  B   C
    a  0  5  10
    b  1  6  11
    c  2  7  12
    d  3  8  13
    e  4  9  14



```python
print(df_wide.melt(id_vars="A", value_vars=list("BC")))
```

       A variable  value
    0  0        B      5
    1  1        B      6
    2  2        B      7
    3  3        B      8
    4  4        B      9
    5  0        C     10
    6  1        C     11
    7  2        C     12
    8  3        C     13
    9  4        C     14



```python
print(df_wide.stack())
```

    a  A     0
       B     5
       C    10
    b  A     1
       B     6
       C    11
    c  A     2
       B     7
       C    12
    d  A     3
       B     8
       C    13
    e  A     4
       B     9
       C    14
    dtype: int64



```python
df_wide = pd.Series([range(3), range(1), range(10)])
print(df_wide)
```

    0                         (0, 1, 2)
    1                               (0)
    2    (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
    dtype: object



```python
print(df_wide.explode())
```

    0    0
    0    1
    0    2
    1    0
    2    0
    2    1
    2    2
    2    3
    2    4
    2    5
    2    6
    2    7
    2    8
    2    9
    dtype: object


## Long to wide
- The method `df.pivot()` creates columns based on unique levels of a given column filled with the corresponding values;
- The method `df.pivot_table()` generalizes `.pivot` to more complex situations where there may be duplicate entries which have to be aggregated. This is related to performing `.groupby()` chained with `.agg()`, but may have different output format;
- The method `df.unstack()` pivots a DataFrame using its index (useful for MultiIndex DataFrames mostly).


```python
df_long = pd.DataFrame({"id": list(range(4))*3, "type": ["A"]*4 + ["B"]*4 + ["C"]*4, "value":range(12)})
print(df_long)
```

        id type  value
    0    0    A      0
    1    1    A      1
    2    2    A      2
    3    3    A      3
    4    0    B      4
    5    1    B      5
    6    2    B      6
    7    3    B      7
    8    0    C      8
    9    1    C      9
    10   2    C     10
    11   3    C     11



```python
print(df_long.pivot(index="id", columns="type", values="value"))
```

    type  A  B   C
    id            
    0     0  4   8
    1     1  5   9
    2     2  6  10
    3     3  7  11



```python
print(df_long.pivot_table(index="type", aggfunc="min"))
```

          id  value
    type           
    A      0      0
    B      0      4
    C      0      8



```python
# equivalent groupby+agg
print(df_long.groupby("type").agg({"value": "min"}))
```

          value
    type       
    A         0
    B         4
    C         8



```python
print(df_long.set_index(["type", "id"]))
```

             value
    type id       
    A    0       0
         1       1
         2       2
         3       3
    B    0       4
         1       5
         2       6
         3       7
    C    0       8
         1       9
         2      10
         3      11



```python
print(df_long.set_index(["type", "id"]).unstack())
```

         value           
    id       0  1   2   3
    type                 
    A        0  1   2   3
    B        4  5   6   7
    C        8  9  10  11



```python
print(df_long.set_index(["id", "type"]).unstack())
```

         value       
    type     A  B   C
    id               
    0        0  4   8
    1        1  5   9
    2        2  6  10
    3        3  7  11


## Merging DataFrames

Here are a few options on how to merge multiple `DataFrame`s together. See [Merge, join, and concatenate](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html?highlight=concatenate) for more details.

## Concatenate

The function `pd.concat([df1, df2])` lets you litteraly concatenate multiple `DataFrame`s along some axis. This function works either as an *inner join* or an *outer join* on the multiple dataframes indices.

The function `df.append(other_df)` does concatenation on the index axis (i.e., add rows)

Using `ignore_index=True` can be useful when you don't want to join on the indices and only really concatenate the dataframes. (This is most likely the way you want to use `.append()`.)

## Merging

The function `pd.merge` lets you perform four types of joins: `left`, `right`, `outer` and `inner` which are closely related to their SQL equivalents. It generalizes `pd.concat` as you can use columns, instead of the index, to perform the join.

The inline version of `pd.merge` is to use the method `.join` on some pre-existing dataframe. 

## Iterating through DataFrames <a class="anchor" id="iter"></a>

If you need to traverse a `DataFrame` row by row, you can use:
- `.iterrows()` to return (index, row as `Series`);
- `.itertuple()` to return (index, named tuple);

In both cases, you can use multiple assignment to catch each element.

Another, possibly better, way to do something to each row is through `df.apply(fun)`. Thus, the manipulation you would do when iterating across rows could be wrapped into a function `fun` applied to each row. This also allows to apply a function by columns using `axis=1`. To apply a function to each cell, you can use `.applymap(fun)`. 


```python
for i, (a, b, c, d) in df.iterrows():
    print(a, b, c, d)
for i, a, b, c, d in df.itertuples():
    print(a, b, c, d)
print(df.apply(sum, 1))
```

    0.0 0 20.0 30.0
    1.0 1 21.0 31.0
    2.0 2 22.0 32.0
    3.0 3 23.0 33.0
    100 4 102 103
    100 5 nan nan
    0.0 0 20.0 30.0
    1.0 1 21.0 31.0
    2.0 2 22.0 32.0
    3.0 3 23.0 33.0
    100 4 102 103
    100 5 nan nan
    a     50.0
    b     54.0
    c     58.0
    d     62.0
    e    309.0
    f      NaN
    dtype: float64


## Functions and Aggregation

We have seen `.apply` and `.applymap` to apply a function row/column-wise or element-wise. The method `.pipe` allows you to chain and control multiple functions. Note that there exists *many* pre-defined functions which can be performed along axes by specifying `axis=0/1/None` for rows/columns/all.

Often, functions applied to rows or columns are aggregation functions. The `.agg`, a.k.a. `.aggregate`, method lets you perform multiple aggregation functions and produce a well-formated output.

The `.agg` methods is particularly useful for grouped dataframes. The `.groupby` method splits a dataframe into many subsets defined by the arguments passed. Then, applying `.agg` to the grouped dataframe applies it to each subset and produces a dataframe where the index defines the subset and the columns define the aggregation functions.

The `.describe` function works as an `.agg` call acting on numerical columns only. This can be particularly useful when computing summary statistics on a dataset. Also, this can be chained with a `groupby` to perform description by subgroups of the data!

## MultiIndex DataFrames

`MultiIndex` works just like regular indices except that they have a structure using levels: instead of a single key, each row has a tuple of values acting as a key. Playing with `MultiIndex` can be cumbersome sometimes so a nice trick to keep in mind is the `.reset_index(inplace=True)` method which moves the MultiIndex to new columns and creates a dummy index in its place. 

## Scikit-learn Transformations

If you need to scale the data (say to mean 0 and variance 1), I suggest to use the `StandardScaler` from `sklearn`. It internally stores the mean and standard deviation used for standardization. Then, if you need to apply the same transformation to another matrix, you can do it easily. Also, if you need to recover the original matrix, you can!


```python
from sklearn.preprocessing import StandardScaler
import numpy as np
X = np.random.uniform(0, 1, (3, 4))
scaler = StandardScaler().fit(X)
print(X)
Xstd = scaler.transform(X)
print(Xstd)
print(scaler.inverse_transform(Xstd))
```

    [[0.27355506 0.52822275 0.51469633 0.06545488]
     [0.44123359 0.69095683 0.52764392 0.44219493]
     [0.61651989 0.99101129 0.12910797 0.3453753 ]]
    [[-1.21558928 -1.0877613   0.6718045  -1.3702373 ]
     [-0.01811033 -0.23879521  0.74183104  0.98816536]
     [ 1.23369961  1.32655652 -1.41363554  0.38207193]]
    [[0.27355506 0.52822275 0.51469633 0.06545488]
     [0.44123359 0.69095683 0.52764392 0.44219493]
     [0.61651989 0.99101129 0.12910797 0.3453753 ]]


Typically, categorical data is not encoded using integers. You can always produce a map to integer yourself but you need to keep track of the map. The `LabelBinarizer` can do that for you! Then, this uniformizes all encoding and ensures you can recover the correct original categories.


```python
from sklearn.preprocessing import LabelBinarizer
y = np.array(["A"]*4 + ["B"]*6)
print(y)
label_encoder = LabelBinarizer(neg_label=0, pos_label=1)
y_01 = label_encoder.fit_transform(y)
print(y_01)
print(label_encoder.inverse_transform(np.array([0, 1, 0, 1, 1, 0, 1])))
```

    ['A' 'A' 'A' 'A' 'B' 'B' 'B' 'B' 'B' 'B']
    [[0]
     [0]
     [0]
     [0]
     [1]
     [1]
     [1]
     [1]
     [1]
     [1]]
    ['A' 'B' 'A' 'B' 'B' 'A' 'B']


Some other interesting transformations (see [Preprocessing and Normalization](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.preprocessing) for many more):
- `LabelEncoder` for more than two categories (one-hot)
- `MultiLabelBinarizer` for multiple labels to 0/1 encoding
