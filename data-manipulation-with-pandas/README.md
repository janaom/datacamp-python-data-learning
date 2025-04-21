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







