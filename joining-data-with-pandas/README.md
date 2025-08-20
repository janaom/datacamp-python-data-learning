# Joining Data with pandas

Being able to combine and work with multiple datasets is an essential skill for any aspiring Data Scientist. pandas is a crucial cornerstone of the Python data science ecosystem, with Stack Overflow recording 5 million views for pandas questions. Learn to handle multiple DataFrames by combining, organizing, joining, and reshaping them using pandas. You'll work with datasets from the World Bank and the City Of Chicago. You will finish the course with a solid skillset for data-joining in pandas.

✅ [Data Merging Basics](https://github.com/janaom/datacamp-python-data-learning/blob/main/joining-data-with-pandas/README.md#data-merging-basics)

✅ Merging Tables With Different Join Types

✅ Advanced Merging and Concatenating

✅ Merging Ordered and Time-Series Data

------------------------
# Data Merging Basics

To help us learn about merging tables, we will use data from the city of Chicago data portal.

The city of Chicago is divided into fifty local neighborhoods called wards. We have a table with data about the local government offices in each ward. In this example, we want to merge the local government data with census data about the population of each ward.

<img width="1079" height="503" alt="image" src="https://github.com/user-attachments/assets/5cfd6bf8-c9de-4354-ad69-2e7937f8ead6" />

<img width="1104" height="491" alt="image" src="https://github.com/user-attachments/assets/eedc8560-f39a-4469-9a17-b65a8d863268" />

The two tables are related by their ward column. We can merge them together, matching the ward number from each row of the wards table to the ward numbers from the census table. For example, the second ward in the wards table with Alderman Brian Hopkins would be matched with row 2 of the census table where the population in 2000 was 54,361.

<img width="1110" height="521" alt="image" src="https://github.com/user-attachments/assets/fef76b51-5df3-4efe-9e06-2c663c969d96" />

The pandas package has an excellent DataFrame method for performing this type of merge called merge. The merge method takes the first DataFrame, wards, and merges it with the second DataFrame, census. We use the on argument to tell the method that we want to merge the two DataFrames on the ward column. Since we listed the wards table first, its columns will appear first in the output, followed by the columns from the census table. In this example, the merge returns a DataFrame with 50 rows and 9 columns, where the returned rows have matching values for the ward column in both tables. This is called an inner join.

<img width="1109" height="518" alt="image" src="https://github.com/user-attachments/assets/36e13415-2b73-468a-8e63-d02213691b4c" />

An inner join will only return rows that have matching values in both tables.

<img width="1079" height="474" alt="image" src="https://github.com/user-attachments/assets/ec31f68f-95c2-4807-8fc4-567c227569cd" />

You may have noticed that the merged table has columns with suffixes of underscore x or y. This is because both the wards and census tables contained address and zip columns. To avoid multiple columns with the same name, they are automatically given a suffix by the merge method.

<img width="1106" height="281" alt="image" src="https://github.com/user-attachments/assets/0157c238-17f7-4706-9658-18a2c8c13329" />

We can use the suffix argument of the merge method to control this behavior. We provide a tuple where all of the overlapping columns in the left table are given the suffix '_ward', and those of the right table will be given the suffix '_cen'. This makes it easier for us to tell the difference between the columns.

<img width="1105" height="461" alt="image" src="https://github.com/user-attachments/assets/f7ccb798-2a33-4dc4-9de4-cce2ee8255aa" />



