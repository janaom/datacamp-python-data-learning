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


Example:

```python
In [2]:
print(taxi_owners.head())
     rid   vid           owner                 address    zip
0  T6285  6285  AGEAN TAXI LLC     4536 N. ELSTON AVE.  60630
1  T4862  4862    MANGIB CORP.  5717 N. WASHTENAW AVE.  60659
2  T1495  1495   FUNRIDE, INC.     3351 W. ADDISON ST.  60618
3  T4231  4231    ALQUSH CORP.   6611 N. CAMPBELL AVE.  60645
4  T5971  5971  EUNIFFORD INC.     3351 W. ADDISON ST.  60618
In [3]:
print(taxi_veh.head())
    vid    make   model  year fuel_type                owner
0  2767  TOYOTA   CAMRY  2013    HYBRID       SEYED M. BADRI
1  1411  TOYOTA    RAV4  2017    HYBRID          DESZY CORP.
2  6500  NISSAN  SENTRA  2019  GASOLINE       AGAPH CAB CORP
3  2746  TOYOTA   CAMRY  2013    HYBRID  MIDWEST CAB CO, INC
4  5922  TOYOTA   CAMRY  2013    HYBRID       SUMETTI CAB CO
```

Q: hoose the column you would use to merge the two tables on using the `.merge()` method.

A: `on='vid'`

## Exercise: Your first inner join

You have been tasked with figuring out what the most popular types of fuel used in Chicago taxis are. To complete the analysis, you need to merge the `taxi_owners` and `taxi_veh` tables together on the `vid` column. You can then use the merged table along with the `.value_counts()` method to find the most common `fuel_type`.

Since you'll be working with `pandas` throughout the course, the package will be preloaded for you as `pd` in each exercise in this course. Also the `taxi_owners` and `taxi_veh` DataFrames are loaded for you.

     Merge taxi_owners with taxi_veh on the column vid, and save the result to taxi_own_veh.
     Set the left and right table suffixes for overlapping columns of the merge to _own and _veh, respectively.
     Select the fuel_type column from taxi_own_veh and print the value_counts() to find the most popular fuel_types used.
     

## Solution

```python
# Merge the taxi_owners and taxi_veh tables
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid')

# Print the column names of the taxi_own_veh
print(taxi_own_veh.columns)

## Results
Index(['rid', 'vid', 'owner_x', 'address', 'zip', 'make', 'model', 'year', 'fuel_type', 'owner_y'], dtype='object')
```

```python
# Merge the taxi_owners and taxi_veh tables setting a suffix
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own', '_veh'))

# Print the column names of taxi_own_veh
print(taxi_own_veh.columns)

##Results
Index(['rid', 'vid', 'owner_own', 'address', 'zip', 'make', 'model', 'year', 'fuel_type', 'owner_veh'], dtype='object')
```

```python
# Merge the taxi_owners and taxi_veh tables setting a suffix
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own','_veh'))

# Print the value_counts to find the most popular fuel_type
print(taxi_own_veh['fuel_type'].value_counts())

##Results
fuel_type
HYBRID                    2792
GASOLINE                   611
FLEX FUEL                   89
COMPRESSED NATURAL GAS      27
Name: count, dtype: int64
```

## Exercise: Inner joins and number of rows returned

All of the merges you have studied to this point are called inner joins. It is necessary to understand that inner joins only return the rows with matching values in both tables. You will explore this further by reviewing the merge between the wards and census tables, then comparing it to merges of copies of these tables that are slightly altered, named wards_altered, and census_altered. The first row of the wards column has been changed in the altered tables. You will examine how this affects the merge between them. The tables have been loaded for you.

For this exercise, it is important to know that the wards and census tables start with 50 rows.

     Merge wards and census on the ward column and save the result to wards_census.
     Merge the wards_altered and census tables on the ward column, and notice the difference in returned rows.
     Merge the wards and census_altered tables on the ward column, and notice the difference in returned rows.

## Solution

```python
# Merge the wards and census tables on the ward column
wards_census = wards.merge(census, on='ward')

# Print the shape of wards_census
print('wards_census table shape:', wards_census.shape)

##Results
wards_census table shape: (50, 9)
```
```python
# Print the first few rows of the wards_altered table to view the change 
print(wards_altered[['ward']].head())

# Merge the wards_altered and census tables on the ward column
wards_altered_census = wards_altered.merge(census, on='ward')

# Print the shape of wards_altered_census
print('wards_altered_census table shape:', wards_altered_census.shape)

##Results
  ward
0   61
1    2
2    3
3    4
4    5
wards_altered_census table shape: (49, 9)
```

```python
# Print the first few rows of the census_altered table to view the change 
print(census_altered[['ward']].head())

# Merge the wards and census_altered tables on the ward column
wards_census_altered = wards.merge(census_altered, on='ward')

# Print the shape of wards_census_altered
print('wards_census_altered table shape:', wards_census_altered.shape)

##Results
   ward
0  None
1     2
2     3
3     4
4     5
wards_census_altered table shape: (49, 9)
```

In the last lesson, we learned how to merge two DataFrames together with the merge method. In this lesson, we'll discuss different types of relationships between tables. In particular, we will discuss the one-to-many relationship. But first, let's quickly consider what a one-to-one relationship is. 

In a one-to-one relationship, every row in the left table is related to one and only one row in the right table. 

<img width="1086" height="351" alt="image" src="https://github.com/user-attachments/assets/9624b089-2f17-435c-87bd-161211d801b5" />

We looked at a one-to-one relationship earlier. Recall the relationship between the wards table and the census table. Every row in the wards table is related to only one row in the census table, so there is only one row for ward 3 in each table. Practically speaking, it only makes sense that there is one row of population information for each ward. It wouldn't make sense if the census table contained multiple population values in 2000 for the third ward. 

<img width="1148" height="546" alt="image" src="https://github.com/user-attachments/assets/4cdbf18c-4807-4b91-8d74-70946b14325e" />

So, what is a one-to-many relationship? Well, in a one-to-many relationship, every row in the left table is related to one or more rows in the right table. 

<img width="1048" height="419" alt="image" src="https://github.com/user-attachments/assets/dac938a7-dacb-4d77-af88-badd5b45ac2a" />

To provide an example of a one-to-many relationship, let's think back to our wards table. Within each ward, there are many businesses. We will merge the wards table with a table of licensed businesses in each ward. 

The business license data is stored in another table called licenses. It holds info such as the business address and ward the business is located within. 

<img width="1151" height="522" alt="image" src="https://github.com/user-attachments/assets/dca06e7d-2537-4a98-8db8-0721d2d7bd22" />

The two DataFrames are related to each other by their ward column. 

<img width="1148" height="547" alt="image" src="https://github.com/user-attachments/assets/f1cd09b8-b771-4cb5-a063-e0c5db277ce7" />

When we merge the two tables together with the merge method, setting the 'on' attribute to the column ward, the resulting table has both local ward data and business license data. Notice that ward 1 and its alderman Joe is repeated in the resulting table because the licenses table has many businesses in the 1st ward. pandas takes care of the one-to-many relationships for us and doesn't require anything special on our end. We can use the same syntax as we did with one-to-one relationships. 

<img width="1154" height="406" alt="image" src="https://github.com/user-attachments/assets/a3993a9c-bebc-44d6-9db0-b72ea23c1210" />

By printing the shape, we can see that our original wards table has 50 rows. After merging the wards table with the licenses table, the resulting table has 10,000 rows. When you merge tables that have a one-to-many relationship, the number of rows returned will likely be different than the number in the left table. 

<img width="1157" height="396" alt="image" src="https://github.com/user-attachments/assets/f1863847-11c7-4098-b0b7-a57eda2f982e" />

## Exercise: One-to-many merge

A business may have one or multiple owners. In this exercise, you will continue to gain experience with one-to-many merges by merging a table of business owners, called biz_owners, to the licenses table. Recall from the video lesson, with a one-to-many relationship, a row in the left table may be repeated if it is related to multiple rows in the right table. In this lesson, you will explore this further by finding out what is the most common business owner title. (i.e., secretary, CEO, or vice president)

The licenses and biz_owners DataFrames are loaded for you.

    Starting with the licenses table on the left, merge it to the biz_owners table on the column account, and save the results to a variable named licenses_owners.
    Group licenses_owners by title and count the number of accounts for each title. Save the result as counted_df
    Sort counted_df by the number of accounts in descending order, and save this as a variable named sorted_df.
    Use the .head() method to print the first few rows of the sorted_df.

## Solution

```python
# Merge the licenses and biz_owners table on account
licenses_owners = licenses.merge(biz_owners, on='account')

# Group the results by title then count the number of accounts
counted_df = licenses_owners.groupby('title').agg({'account':'count'})

# Sort the counted_df in descending order
sorted_df = counted_df.sort_values(by='account', ascending=False)

# Use .head() method to print the first few rows of sorted_df
print(sorted_df.head())

##Results
                 account
title                   
PRESIDENT           6259
SECRETARY           5205
SOLE PROPRIETOR     1658
OTHER               1200
VICE PRESIDENT       970
```

In our last lesson, we learned how to merge two tables with a one-to-many relationship using the merge method. Merging data like this is a necessary skill to bring together data from different sources to answer some more complex data questions. 

Sometimes we need to merge together more than just two tables to complete our analysis. 

<img width="1165" height="550" alt="image" src="https://github.com/user-attachments/assets/0dd779a0-055d-4e49-ae0e-06ea1ee55903" />

In the previous lesson, we used two tables from the city of Chicago. One table contained business licenses issued by the city. 

<img width="1138" height="405" alt="image" src="https://github.com/user-attachments/assets/f7ff8080-c1be-4d72-9807-a49a8a7c7823" />

The other table listed info about the local neighborhoods called wards, including the local government official's office. 

<img width="1138" height="402" alt="image" src="https://github.com/user-attachments/assets/6738d463-5e3e-4337-b9b1-fb38a65cb25c" />

Now, we also have a table of businesses that have received small business grant money from Chicago. The grants are funded by taxpayer money. Therefore, it would be helpful to analyze how much grant money each business received and in what ward that business is located. We then could determine if one ward's businesses received a disproportionately large amount of grant money.

<img width="1126" height="440" alt="image" src="https://github.com/user-attachments/assets/4b648415-4f98-4ae5-acca-982194a7c707" />

To pull all of this information together, let's first connect our grants table to our licenses table. The two tables are related by their company name and location. Let's pause here for a moment. 

<img width="1141" height="528" alt="image" src="https://github.com/user-attachments/assets/425414c9-ff1a-4ddc-862a-1dadb6ef32c4" />

If we merge the two tables only using the zip column, then the 60616 zip of Reggie's bar from the licenses table will be matched to multiple businesses in the grants table with the same zip. Our code sample prints the first few rows and some columns of the merged table. The output of the merge duplicates Reggie's bar for each matching zip in the grants table, which is not what we want. If instead, we merged on address only, there's a small risk that the address would repeat in different parts of the city. Therefore, the best option is to merge the tables using the combination of both address and zip code. 

<img width="1140" height="396" alt="image" src="https://github.com/user-attachments/assets/9c910f4c-bd89-4cbf-9cbe-4b77d601487b" />

We merge the two DataFrames as shown before, except in this case, we pass a list of the column names we want to merge on to the 'on' argument. This allows us to use multiple columns in the merge. As before, the matching rows between the two DataFrames are returned with the columns from the grant table listed first. However, when we merge on two columns, in this case address and zip code, we are requiring that both the address and zip code of a row in the left table match the address and zip code of a row in the right table in order for them to be linked to each other in the merge. 

<img width="1131" height="378" alt="image" src="https://github.com/user-attachments/assets/8dd6ecd9-6da0-40be-bf5d-a06b460a1104" />

We can now extend this example to a third table. First, we merge the grants table with the wards table on the ward column again, adding suffixes to the repeated column names. Note that we're using Python's backslash line continuation method to add the second merge on the next line. Python will read this as just one line of code. Without this, Python will throw a syntax error since it will parse it as two separate lines of code, so don't forget your backslash. Now our output table has information about grants, business, and wards. We can now complete our analysis. 

<img width="1134" height="432" alt="image" src="https://github.com/user-attachments/assets/b6372d8d-8a4f-43ae-a723-be94eafb4388" />

We can now sum the grants by ward and plot the results. Some wards have received more grants than others. 

<img width="1129" height="528" alt="image" src="https://github.com/user-attachments/assets/9b7e79e1-8c96-4928-9adb-f87d74461378" />

We could continue to merge additional tables as needed. We stopped at three, but if needed, we could continue to add more. The code here shows the pattern you would follow as you merge more tables. 

<img width="1134" height="458" alt="image" src="https://github.com/user-attachments/assets/72a3d16f-b4f0-4dca-92fb-22390eb04641" />


## Exercise: Total riders in a month

Your goal is to find the total number of rides provided to passengers passing through the Wilson station (station_name == 'Wilson') when riding Chicago's public transportation system on weekdays (day_type == 'Weekday') in July (month == 7). Luckily, Chicago provides this detailed data, but it is in three different tables. You will work on merging these tables together to answer the question. This data is different from the business related data you have seen so far, but all the information you need to answer the question is provided.

The cal, ridership, and stations DataFrames have been loaded for you. The relationship between the tables can be seen in the diagram below.

<img width="1968" height="782" alt="cta_L_diagram" src="https://github.com/user-attachments/assets/38ff9f44-f155-40fc-8687-d2acb3323a05" />

     Merge the ridership and cal tables together, starting with the ridership table on the left and save the result to the variable ridership_cal. If you code takes too long to run, your merge conditions might be incorrect.
     Extend the previous merge to three tables by also merging the stations table.
     Create a variable called filter_criteria to select the appropriate rows from the merged table so that you can sum the rides column.


## Solution

```python
# Merge the ridership and cal tables
ridership_cal = ridership.merge(cal)

# Merge the ridership, cal, and stations tables
ridership_cal_stations = ridership.merge(cal, on=['year','month','day']) \
            				.merge(stations)

# Merge the ridership, cal, and stations tables
ridership_cal_stations = ridership.merge(cal, on=['year','month','day']) \
							.merge(stations, on='station_id')

# Create a filter to filter ridership_cal_stations
filter_criteria = ((ridership_cal_stations['month'] == 7) 
                   & (ridership_cal_stations['day_type'] == 'Weekday') 
                   & (ridership_cal_stations['station_name'] == 'Wilson'))

# Use .loc and the filter to select for rides
print(ridership_cal_stations.loc[filter_criteria, 'rides'].sum())

##Results
140005
```

## Exercise: Three table merge

To solidify the concept of a three DataFrame merge, practice another exercise. A reasonable extension of our review of Chicago business data would include looking at demographics information about the neighborhoods where the businesses are. A table with the median income by zip code has been provided to you. You will merge the licenses and wards tables with this new income-by-zip-code table called zip_demo.

The licenses, wards, and zip_demo DataFrames have been loaded for you.


    Starting with the licenses table, merge to it the zip_demo table on the zip column. Then merge the resulting table to the wards table on the ward column. Save result of the three merged tables to a variable named licenses_zip_ward.
    Group the results of the three merged tables by the column alderman and find the median income.

 ## Solution

 ```python
# Merge licenses and zip_demo, on zip; and merge the wards on ward
licenses_zip_ward = licenses.merge(zip_demo, on='zip') \
            			.merge(wards, on='ward') 

# Print the results by alderman and show median income
print(licenses_zip_ward.groupby('alderman').agg({'income':'median'}))

##Results
                             income
alderman                           
Ameya Pawar                 66246.0
Anthony A. Beale            38206.0
Anthony V. Napolitano       82226.0
Ariel E. Reyboras           41307.0
Brendan Reilly             110215.0
Brian Hopkins               87143.0
Carlos Ramirez-Rosa         66246.0
Carrie M. Austin            38206.0
Chris Taliaferro            55566.0
Daniel "Danny" Solis        41226.0
David H. Moore              33304.0
Deborah Mell                66246.0
Debra L. Silverstein        50554.0
Derrick G. Curtis           65770.0
Edward M. Burke             42335.0
Emma M. Mitts               36283.0
George Cardenas             33959.0
Gilbert Villegas            41307.0
Gregory I. Mitchell         24941.0
Harry Osterman              45442.0
Howard B. Brookins, Jr.     33304.0
James Cappleman             79565.0
Jason C. Ervin              41226.0
Joe Moore                   39163.0
John S. Arena               70122.0
Leslie A. Hairston          28024.0
Margaret Laurino            70122.0
Marty Quinn                 67045.0
Matthew J. O'Shea           59488.0
Michael R. Zalewski         42335.0
Michael Scott, Jr.          31445.0
Michelle A. Harris          32558.0
Michelle Smith             100116.0
Milagros "Milly" Santiago   41307.0
Nicholas Sposato            62223.0
Pat Dowell                  46340.0
Patrick Daley Thompson      41226.0
Patrick J. O'Connor         50554.0
Proco "Joe" Moreno          87143.0
Raymond A. Lopez            33959.0
Ricardo Munoz               31445.0
Roberto Maldonado           68223.0
Roderick T. Sawyer          32558.0
Scott Waguespack            68223.0
Susan Sadlowski Garza       38417.0
Tom Tunney                  88708.0
Toni L. Foulkes             27573.0
Walter Burnett, Jr.         87143.0
William D. Burns           107811.0
Willie B. Cochran           28024.0
```

## Exercise: One-to-many merge with multiple tables

In this exercise, assume that you are looking to start a business in the city of Chicago. Your perfect idea is to start a company that uses goats to mow the lawn for other businesses. However, you have to choose a location in the city to put your goat farm. You need a location with a great deal of space and relatively few businesses and people around to avoid complaints about the smell. You will need to merge three tables to help you choose your location. The land_use table has info on the percentage of vacant land by city ward. The census table has population by ward, and the licenses table lists businesses by ward.

The land_use, census, and licenses tables have been loaded for you.

	Merge land_use and census on the ward column. Merge the result of this with licenses on the ward column, using the suffix _cen for the left table and _lic for the right table. Save this to the variable land_cen_lic.
	Group land_cen_lic by ward, pop_2010 (the population in 2010), and vacant, then count the number of accounts. Save the results to pop_vac_lic.
  	Sort pop_vac_lic by vacant, account, andpop_2010 in descending, ascending, and ascending order respectively. Save it as sorted_pop_vac_lic.

 ## Solution

 ```python
# Merge land_use and census and merge result with licenses including suffixes
land_cen_lic = land_use.merge(census, on='ward') \
				.merge(licenses, on='ward', suffixes=('_cen','_lic'))
```
```python
# Merge land_use and census and merge result with licenses including suffixes
land_cen_lic = land_use.merge(census, on='ward') \
                    .merge(licenses, on='ward', suffixes=('_cen','_lic'))

# Group by ward, pop_2010, and vacant, then count the # of accounts
pop_vac_lic = land_cen_lic.groupby(['ward', 'pop_2010', 'vacant'], 
                                   as_index=False).agg({'account':'count'})
```
```python
# Merge land_use and census and merge result with licenses including suffixes
land_cen_lic = land_use.merge(census, on='ward') \
                    .merge(licenses, on='ward', suffixes=('_cen','_lic'))

# Group by ward, pop_2010, and vacant, then count the # of accounts
pop_vac_lic = land_cen_lic.groupby(['ward','pop_2010','vacant'], 
                                   as_index=False).agg({'account':'count'})

# Sort pop_vac_lic and print the results
sorted_pop_vac_lic = pop_vac_lic.sort_values(by=['vacant', 'account', 'pop_2010'], 
                                             ascending=[False, True, True])

# Print the top few rows of sorted_pop_vac_lic
print(sorted_pop_vac_lic.head())

##Results
   ward  pop_2010  vacant  account
47    7     51581      19       80
12   20     52372      15      123
1    10     51535      14      130
16   24     54909      13       98
7    16     51954      13      156
```
