### Grouping and Sorting
#### Introduction
Maps allow us to transform data in a DataFrame or Series one value at a time for an entire column. However, often we want to group our data, and then do something specific to the group the data is in.

As we'll learn, we do this with the groupby() operation. We'll also cover some additional topics, such as more complex ways to index our DataFrames, along with how to sort our data.

#### Groupwise analysis
One function we've been using heavily thus far is the value_counts() function. We can replicate what value_counts() does by doing the following:
```python
data.groupby('points').points.count()
```
groupby() created a group of reviews which allotted the same point values to the given wines. Then, for each of these groups, we grabbed the points() column and counted how many times it appeared. value_counts() is just a shortcut to this groupby() operation.

We can use any of the summary functions we've used before with this data. For example, to get the cheapest wine in each point value category, we can do the following:
```python
reviews.groupby('points').price.min()
```

