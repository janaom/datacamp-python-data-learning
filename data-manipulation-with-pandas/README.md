# Data Manipulation with pandas

pandas is the world's most popular Python library, used for everything from data manipulation to data analysis. In this course, you'll learn how to manipulate DataFrames, as you extract, filter, and transform real-world datasets for analysis. Using pandas you’ll explore all the core data science concepts. Using real-world data, including Walmart sales figures and global temperature time series, you’ll learn how to import, clean, calculate statistics, and create visualizations—using pandas to add to the power of Python!

---------------

Transforming DataFrames

Aggregating DataFrames

Slicing and Indexing DataFrames

Creating and Visualizing DataFrames

---------------------

# Transforming DataFrames

pandas is a Python package for data manipulation. It can also be used for data visualization. 

pandas is built on top of two essential Python packages, NumPy and Matplotlib. Numpy provides multidimensional array objects for easy data manipulation that pandas uses to store data, and Matplotlib has powerful data visualization capabilities that pandas takes advantage of.

In pandas, rectangular data is represented as a DataFrame object. Every programming language used for data analysis has something similar to this. R also has DataFrames, while SQL has database tables. Every value within a column has the same data type, either text or numeric, but different columns can contain different data types. 

When you first receive a new dataset, you want to quickly explore it and get a sense of its contents. pandas has several methods for this. The first is head, which returns the first few rows of the DataFrame. We only had seven rows to begin with, so it's not super exciting, but this becomes very useful if you have many rows. 

![image](https://github.com/user-attachments/assets/fb0b62ca-071d-4822-bbbb-1c0ba10350d1)

The info method displays the names of columns, the data types they contain, and whether they have any missing values. 

![image](https://github.com/user-attachments/assets/6b394351-45ff-4147-b30c-5475f67aacb2)

A DataFrame's shape attribute contains a tuple that holds the number of rows followed by the number of columns. Since this is an attribute instead of a method, you write it without parentheses. 

![image](https://github.com/user-attachments/assets/ff14c779-19d7-4a7c-a8e4-b0283e6780a1)

The describe method computes some summary statistics for numerical columns, like mean and median. "count" is the number of non-missing values in each column. describe is good for a quick overview of numeric variables, but if you want more control, you'll see how to perform more specific calculations later in the course. 

![image](https://github.com/user-attachments/assets/1611a817-21cb-4d93-84e9-96458ee1955b)

DataFrames consist of three different components, accessible using attributes. The values attribute, as you might expect, contains the data values in a 2-dimensional NumPy array. 

![image](https://github.com/user-attachments/assets/f73f9322-09dd-43c9-9443-9f60ce1bfd4f)

The other two components of a DataFrame are labels for columns and rows. The columns attribute contains column names, and the index attribute contains row numbers or row names. Be careful, since row labels are stored in dot-index, not in dot-rows. Notice that these are Index objects. This allows for flexibility in labels. For example, the dogs data uses row numbers, but row names are also possible. 

![image](https://github.com/user-attachments/assets/e884b1e1-a6f3-4353-9aff-07722ca9997a)


## Exercise: Inspecting a DataFrame



When you get a new DataFrame to work with, the first thing you need to do is explore it and see what it contains. There are several useful methods and attributes for this.

    .head() returns the first few rows (the “head” of the DataFrame).
    .info() shows information on each of the columns, such as the data type and number of missing values.
    .shape returns the number of rows and columns of the DataFrame.
    .describe() calculates a few summary statistics for each column.

homelessness is a DataFrame containing estimates of homelessness in each U.S. state in 2018. The individual column is the number of homeless individuals not part of a family with children. The family_members column is the number of homeless individuals part of a family with children. The state_pop column is the state's total population.

pandas is imported for you.

## Solution

Print the head of the homelessness DataFrame.

```python
# Print the head of the homelessness data
print(homelessness.head())

#Result
               region       state  individuals  family_members  state_pop
0  East South Central     Alabama       2570.0           864.0    4887681
1             Pacific      Alaska       1434.0           582.0     735139
2            Mountain     Arizona       7259.0          2606.0    7158024
3  West South Central    Arkansas       2280.0           432.0    3009733
4             Pacific  California     109008.0         20964.0   39461588
```

Print information about the column types and missing values in homelessness.

```python
# Print information about homelessness
print(homelessness.info())

#Result
<class 'pandas.core.frame.DataFrame'>
Int64Index: 51 entries, 0 to 50
Data columns (total 5 columns):
 #   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
 0   region          51 non-null     object 
 1   state           51 non-null     object 
 2   individuals     51 non-null     float64
 3   family_members  51 non-null     float64
 4   state_pop       51 non-null     int64  
dtypes: float64(2), int64(1), object(2)
memory usage: 2.4+ KB
None
```

Print the number of rows and columns in homelessness.

```python
# Print the shape of homelessness
print(homelessness.shape)

#Result
(51, 5)
```

Print some summary statistics that describe the homelessness DataFrame.

```python
# Print a description of homelessness
print(homelessness.describe())

#Result
       individuals  family_members  state_pop
count       51.000          51.000  5.100e+01
mean      7225.784        3504.882  6.406e+06
std      15991.025        7805.412  7.327e+06
min        434.000          75.000  5.776e+05
25%       1446.500         592.000  1.777e+06
50%       3082.000        1482.000  4.461e+06
75%       6781.500        3196.000  7.341e+06
max     109008.000       52070.000  3.946e+07
```
