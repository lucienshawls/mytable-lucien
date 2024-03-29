# Package `mytable-lucien`
A simple package for processing data in the form of a table.

Pay attention, *all indexes start from 0 instead of 1*.

To install:
```shell
pip install mytable-lucien
```
To import:
```python
import mytable_lucien
```
## Module `mycsv`
This is a simple reader and writer for CSV files by Lucien Shaw. It consumes less resource and processes more quickly than the current csv module, though a lot less functional.

It reads CSV files as plain texts and stores the table in a list, whose elements are lists of cells of the current row. The list is the value to the key 'full' of a dict, which is the returned value of the function.

Here is the guidance.
### Import
```python
from mytable_lucien import mycsv
```
### Function `read()`
This reads a CSV file and store the table in a list.
- Usage
  ```python
  res = mycsv.read(filename, delimiter=',')
  ```
- Arguments
  - `filename`  
    A string value. The filename of the CSV file.
  - `delimiter`  
    A char value. Comma by default. The character which is used to delimit the columns.
- Returned value  
  List of rows. Each row is a list of columns, aka. cells, which contains strings. 
### Function `write()`
This creates a CSV file.
- Usage
  ```python
  mycsv.write(filename, table, delimiter=',')
  ```
- Arguments
  - `filename`  
    A string value. The filename of the CSV file to be written.
  - `table`  
    A list, the structure of which is the same as the value to the key 'full' of the returned dict of function read().  
    All values should be **string**s.
  - `delimiter`  
    A char value. Comma by default. The character which is used to delimit the columns.
- Returned value  
  There are no returned values.
## Module `mytools`
Useful tools. Simple, yet powerful.
### Import
  ```python
  from mytable_lucien import mytools
  ```
### Function `excel_ctn()`
All functions of this package use numbers as indexes, but Excel uses alphabets as indications of the columns, such as 'A' for column 0 (*We count from 0, remember?*), 'Z' for column 25, and 'AA' for column 26.

This converts the alphabetical column Characters To pure Numbers.
- Usage
  ```python
  res = mytools.excel_ctn(col)
  ```
- Arguments
  - `col`  
    Alphabetical column characters, such as 'A' or 'AA', etc.
- Returned value  
  A number, as mentioned above.
## Module `myview`
This provides a better view of the tables.
### Import
```python
from mytable_lucien import myview
```
### Function `select_range()`
In some circumstances, there are so many columns that they cannot be fully displayed in excel, and columns that exceed the limit cannot be visualized.

This allows you to select some columns and rows so that you can extract them to a new temporary CSV file and view them with your favorite table viewer, like Excel.
- Usage
  ```python
  table_select = myview.select_range(table, columns=[], rows=[])
  ```
- Arguments
  - `table`  
    An original table in the form of a list.
  - `columns`  
    A list of column numbers that indicate the columns you would like to see. The default value is an empty list, which selects all columns.
  - `rows`  
    A list of row numbers that indicate the rows you would like to see. The default value is an empty list, which selects all rows.
- Returned value  
  A table which contains the selected range. 
## Module `myedit`
Edit the table the easy way.
### Import
```python
from mytable_lucien import myedit
```
### Function `combine_rows()`
This combines rows of multiple tables with the same total number of columns.
- Usage
  ```python
  comb = myedit.combine_rows(tables)
  ```
- Arguments
  - `tables`  
    A list which contains multiple tables.
- Returned value  
  The combined table.
### Function `combine_columns()`
This combines columns of multiple tables with the same total number of rows.
- Usage
  ```python
  comb = myedit.combine_columns(tables)
  ```
- Arguments
  - `tables`  
    A list which contains multiple tables.
- Returned value  
  The combined table.
