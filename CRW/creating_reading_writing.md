## Creating, Reading and Writing
### Creating Data
There are two core objects in pandas, they are __DataFrame__ and __Series__.

#### What is DataFrame?
It is a table which contains array of individual entries, each of which has certain _value_. Each entry corresponds to a row (_or record_) and _column_.

consider the following example of _DataFrame_:
```python
pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})
```

<img src="/Users/oktavianu/Documents/pandas/CRW/DF-1.png", alt="example of DataFrame">

Pandas DataFrame is not limited to integers. Here is an example of pandas' DataFrame with labels:
```python
pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'],
              'Sue': ['Pretty good.', 'Bland.']},
              index=['Product A', 'Product B'])

```
Based on both example, we use ```pd.DataFrame()``` constructor to generate DataFrame objects. The syntax for declaring a new one is a dictionary whose keys are the column names (```Bob``` and ```Sue``` in this example), and whose values are a list of entries. This is the standard way of constructing a new DataFrame, and the one we are most likely to encounter.

The dictionary-list constructor assigns values to the _column labels_, but just uses an ascending count from 0 (0, 1, 2, 3, ...) for the row labels.

#### What is Series?
By contrast to *__DataFrame__*, *__Series__* is a sequence of data values. If _DataFrame_ is a table, a _Series_ is a list. So we can, in fact create one with nothing more than a list:
```python
pd.Series([1, 2, 3, 4, 5])
```
A Series is, in essence, a single column of a DataFrame. So you can assign row labels to the Series the same way as before, using an ```index``` parameter. However, a Series does not have a column name, it only has one overall ```name```:
```python
pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')
```
The ```Series``` and the ```DataFrame``` are intimately related. It's helpful to think of a ```DataFrame``` as actually being just a bunch of ```Series``` "glued together". 

---
### Reading Data
Being able to create a DataFrame or Series by hand is handy. But, most of the time, we won't actually be creating our own data by hand. Instead, we'll be working with data that already exists.

Data can be stored in any of a number of different forms and formats. By far the most basic of these is the humble CSV file. When you open a CSV file you get something that looks like this:
```
Product A,Product B,Product C,
30,21,9,
35,34,1,
41,11,11
```
So a CSV file is a table of values separated by commas. Hence the name: "Comma-Separated Values", or CSV.

Let's now set aside our toy datasets and see what a real dataset looks like when we read it into a DataFrame. We'll use the ```pd.read_csv()``` function to read the data into a DataFrame. This goes thusly:
```python
variable_name = pd.read_csv("our_filename.csv")
```
We can use the shape attribute to check how large the resulting DataFrame is:
```
variable_name.shape
```
We can examine the contents of the resultant DataFrame using the head() command, which grabs the first five rows:
```
variable_name.head()
```
The ```pd.read_csv()``` function is well-endowed, with over 30 optional parameters we can specify. For example, we can see in this dataset that the CSV file has a built-in index, which pandas did not pick up on automatically. To make pandas use that column for the index (instead of creating a new one from scratch), we can specify an ```index_col```.
```python
variable_name = pd.read_csv("our_filename.csv", index_col=0)
wine_reviews.head()
```
---
### Writing Data
