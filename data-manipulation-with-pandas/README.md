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

## Exercise: Parts of a DataFrame



To better understand DataFrame objects, it's useful to know that they consist of three components, stored as attributes:

    .values: A two-dimensional NumPy array of values.
    .columns: An index of columns: the column names.
    .index: An index for the rows: either row numbers or row names.

You can usually think of indexes as a list of strings or numbers, though the pandas Index data type allows for more sophisticated options. (These will be covered later in the course.)

homelessness is available.


    Import pandas using the alias pd.
    Print a 2D NumPy array of the values in homelessness.
    Print the column names of homelessness.
    Print the index of homelessness.

## Solution

```python
# Import pandas using the alias pd
import pandas as pd

# Print the values of homelessness
print(homelessness.values)

[['East South Central' 'Alabama' 2570.0 864.0 4887681]
 ['Pacific' 'Alaska' 1434.0 582.0 735139]
 ['Mountain' 'Arizona' 7259.0 2606.0 7158024]
 ['West South Central' 'Arkansas' 2280.0 432.0 3009733]
 ['Pacific' 'California' 109008.0 20964.0 39461588]
 ['Mountain' 'Colorado' 7607.0 3250.0 5691287]
 ['New England' 'Connecticut' 2280.0 1696.0 3571520]
 ['South Atlantic' 'Delaware' 708.0 374.0 965479]
 ['South Atlantic' 'District of Columbia' 3770.0 3134.0 701547]
 ['South Atlantic' 'Florida' 21443.0 9587.0 21244317]
 ['South Atlantic' 'Georgia' 6943.0 2556.0 10511131]
 ['Pacific' 'Hawaii' 4131.0 2399.0 1420593]
 ['Mountain' 'Idaho' 1297.0 715.0 1750536]
 ['East North Central' 'Illinois' 6752.0 3891.0 12723071]
 ['East North Central' 'Indiana' 3776.0 1482.0 6695497]
 ['West North Central' 'Iowa' 1711.0 1038.0 3148618]
 ['West North Central' 'Kansas' 1443.0 773.0 2911359]
 ['East South Central' 'Kentucky' 2735.0 953.0 4461153]
 ['West South Central' 'Louisiana' 2540.0 519.0 4659690]
 ['New England' 'Maine' 1450.0 1066.0 1339057]
 ['South Atlantic' 'Maryland' 4914.0 2230.0 6035802]
 ['New England' 'Massachusetts' 6811.0 13257.0 6882635]
 ['East North Central' 'Michigan' 5209.0 3142.0 9984072]
 ['West North Central' 'Minnesota' 3993.0 3250.0 5606249]
 ['East South Central' 'Mississippi' 1024.0 328.0 2981020]
 ['West North Central' 'Missouri' 3776.0 2107.0 6121623]
 ['Mountain' 'Montana' 983.0 422.0 1060665]
 ['West North Central' 'Nebraska' 1745.0 676.0 1925614]
 ['Mountain' 'Nevada' 7058.0 486.0 3027341]
 ['New England' 'New Hampshire' 835.0 615.0 1353465]
 ['Mid-Atlantic' 'New Jersey' 6048.0 3350.0 8886025]
 ['Mountain' 'New Mexico' 1949.0 602.0 2092741]
 ['Mid-Atlantic' 'New York' 39827.0 52070.0 19530351]
 ['South Atlantic' 'North Carolina' 6451.0 2817.0 10381615]
 ['West North Central' 'North Dakota' 467.0 75.0 758080]
 ['East North Central' 'Ohio' 6929.0 3320.0 11676341]
 ['West South Central' 'Oklahoma' 2823.0 1048.0 3940235]
 ['Pacific' 'Oregon' 11139.0 3337.0 4181886]
 ['Mid-Atlantic' 'Pennsylvania' 8163.0 5349.0 12800922]
 ['New England' 'Rhode Island' 747.0 354.0 1058287]
 ['South Atlantic' 'South Carolina' 3082.0 851.0 5084156]
 ['West North Central' 'South Dakota' 836.0 323.0 878698]
 ['East South Central' 'Tennessee' 6139.0 1744.0 6771631]
 ['West South Central' 'Texas' 19199.0 6111.0 28628666]
 ['Mountain' 'Utah' 1904.0 972.0 3153550]
 ['New England' 'Vermont' 780.0 511.0 624358]
 ['South Atlantic' 'Virginia' 3928.0 2047.0 8501286]
 ['Pacific' 'Washington' 16424.0 5880.0 7523869]
 ['South Atlantic' 'West Virginia' 1021.0 222.0 1804291]
 ['East North Central' 'Wisconsin' 2740.0 2167.0 5807406]
 ['Mountain' 'Wyoming' 434.0 205.0 577601]]

# Print the column index of homelessness
print(homelessness.columns)

Index(['region', 'state', 'individuals', 'family_members', 'state_pop'], dtype='object')

# Print the row index of homelessness
print(homelessness.index)

Int64Index([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48,
            49, 50],
           dtype='int64')

```

We'll cover the two simplest and possibly most important ways to find interesting parts of your DataFrame. 

The first thing you can do is change the order of the rows by sorting them so that the most interesting data is at the top of the DataFrame. You can sort rows using the sort_values method, passing in a column name that you want to sort by. For example, when we apply sort_values on the weight_kg column of the dogs DataFrame, we get the lightest dog at the top, Stella the Chihuahua, and the heaviest dog at the bottom, Bernie the Saint Bernard. 

![image](https://github.com/user-attachments/assets/883efd4a-66d0-4bc8-8146-2aa9be77d9f9)

Setting the ascending argument to False will sort the data the other way around, from heaviest dog to lightest dog. 

![image](https://github.com/user-attachments/assets/9e21e536-d134-4da9-87c7-067f151960ff)

We can sort by multiple variables by passing a list of column names to sort_values. Here, we sort first by weight, then by height. Now, Charlie, Lucy, and Bella are ordered from shortest to tallest, even though they all weigh the same. 

![image](https://github.com/user-attachments/assets/2a36e8e1-abd5-4334-844c-94af084364e1)

To change the direction values are sorted in, pass a list to the ascending argument to specify which direction sorting should be done for each variable. Now, Charlie, Lucy, and Bella are ordered from tallest to shortest. 

![image](https://github.com/user-attachments/assets/ea1a2189-fc6b-4050-8d0d-28470df58549)

We may want to zoom in on just one column. We can do this using the name of the DataFrame, followed by square brackets with a column name inside. Here, we can look at just the name column. 

![image](https://github.com/user-attachments/assets/1f92231c-3dd7-4fc5-9619-027eaae559ab)

To select multiple columns, you need two pairs of square brackets. In this code, the inner and outer square brackets are performing different tasks. The outer square brackets are responsible for subsetting the DataFrame, and the inner square brackets are creating a list of column names to subset. This means you could provide a separate list of column names as a variable and then use that list to perform the same subsetting. Usually, it's easier to do in one line. 

![image](https://github.com/user-attachments/assets/32c33a00-5193-49b7-b27f-5138cb7e1c20)

There are lots of different ways to subset rows. The most common way to do this is by creating a logical condition to filter against. For example, let's find all the dogs whose height is greater than 50 centimeters. Now we have a True or False value for every row. 

![image](https://github.com/user-attachments/assets/6265ac89-ce01-4f40-81a3-db7c7b36297a)

We can use the logical condition inside of square brackets to subset the rows we're interested in to get all of the dogs taller than 50 centimeters. 

![image](https://github.com/user-attachments/assets/6bd53e0b-648b-4866-9e37-faca8dc9bcdb)

We can also subset rows based on text data. Here, we use the double equal sign in the logical condition to filter the dogs that are Labradors. 

![image](https://github.com/user-attachments/assets/88d4df76-30ce-4926-b572-6625b579c39d)

We can also subset based on dates. Here, we filter all the dogs born before 2015. Notice that the dates are in quotes and are written as year then month, then day. This is the international standard date format. 

![image](https://github.com/user-attachments/assets/0c25d1b9-8944-4046-a801-56a6e2d457b2)

To subset the rows that meet multiple conditions, you can combine conditions using logical operators, such as the "and" operator seen here. This means that only rows that meet both of these conditions will be subsetted. You could also do this in one line of code, but you'll also need to add parentheses around each condition. 

![image](https://github.com/user-attachments/assets/e1cb9b70-8b36-40ba-b36f-41ba11953654)

If you want to filter on multiple values of a categorical variable, the easiest way is to use the isin method. This takes in a list of values to filter for. Here, we check if the color of a dog is black or brown, and use this condition to subset the data. 

![image](https://github.com/user-attachments/assets/76110037-a9ef-449a-b6b9-f43868e62e05)


## Exercise: Sorting rows


Finding interesting bits of data in a DataFrame is often easier if you change the order of the rows. You can sort the rows by passing a column name to .sort_values().

In cases where rows have the same value (this is common if you sort on a categorical variable), you may wish to break the ties by sorting on another column. You can sort on multiple columns in this way by passing a list of column names.

<img width="738" height="141" alt="image" src="https://github.com/user-attachments/assets/016f373b-4913-4b9e-932d-87c709ae1d89" />


By combining .sort_values() with .head(), you can answer questions in the form, "What are the top cases where…?".

homelessness is available and pandas is loaded as pd.

## Solution

```SQL
1)
# Sort homelessness by the number of homeless individuals in the individuals column, from smallest to largest, and save this as homelessness_ind.
# Print the head of the sorted DataFrame.

# Sort homelessness by individuals
homelessness_ind = homelessness.sort_values("individuals")

# Print the top few rows
print(homelessness_ind.head())

# Results
                region         state  individuals  family_members  state_pop
50            Mountain       Wyoming        434.0           205.0     577601
34  West North Central  North Dakota        467.0            75.0     758080
7       South Atlantic      Delaware        708.0           374.0     965479
39         New England  Rhode Island        747.0           354.0    1058287
45         New England       Vermont        780.0           511.0     624358

2)
# Sort homelessness by the number of homeless family_members in descending order, and save this as homelessness_fam.

# Sort homelessness by descending family members
homelessness_fam = homelessness.sort_values("family_members", ascending=False)

# Print the top few rows
print(homelessness_fam.head())

# Results
                region          state  individuals  family_members  state_pop
32        Mid-Atlantic       New York      39827.0         52070.0   19530351
4              Pacific     California     109008.0         20964.0   39461588
21         New England  Massachusetts       6811.0         13257.0    6882635
9       South Atlantic        Florida      21443.0          9587.0   21244317
43  West South Central          Texas      19199.0          6111.0   28628666

3)
# Sort homelessness first by region (ascending), and then by number of family members (descending). Save this as homelessness_reg_fam.

# Sort homelessness by region, then descending family members
homelessness_reg_fam = homelessness.sort_values(["region", "family_members"], ascending=[True, False])

# Print the top few rows
print(homelessness_reg_fam.head())

# Results
                region      state  individuals  family_members  state_pop
13  East North Central   Illinois       6752.0          3891.0   12723071
35  East North Central       Ohio       6929.0          3320.0   11676341
22  East North Central   Michigan       5209.0          3142.0    9984072
49  East North Central  Wisconsin       2740.0          2167.0    5807406
14  East North Central    Indiana       3776.0          1482.0    6695497
```

## Exercise: Subsetting columns

When working with data, you may not need all of the variables in your dataset. Square brackets ([]) can be used to select only the columns that matter to you in an order that makes sense to you. To select only "col_a" of the DataFrame df, use

```SQL
df["col_a"]
```

To select "col_a" and "col_b" of df, use

```SQL
df[["col_a", "col_b"]]
```

homelessness is available and pandas is loaded as pd.

## Solution

```SQL

1)
# Create a Series called individuals that contains only the individuals column of homelessness.

# Select the individuals column
individuals = homelessness["individuals"]

print(individuals.head())

# Results
0      2570.0
1      1434.0
2      7259.0
3      2280.0
4    109008.0
Name: individuals, dtype: float64

2)
# Create a DataFrame called state_fam that contains only the state and family_members columns of homelessness, in that order.

# Select the state and family_members columns
state_fam = homelessness[["state", "family_members"]]

print(state_fam.head())

# Results
        state  family_members
0     Alabama           864.0
1      Alaska           582.0
2     Arizona          2606.0
3    Arkansas           432.0
4  California         20964.0

3)
# Create a DataFrame called ind_state that contains the individuals and state columns of homelessness, in that order.

# Select only the individuals and state columns, in that order
ind_state = homelessness[["individuals", "state"]]

print(ind_state.head())

# Results
       individuals       state
    0       2570.0     Alabama
    1       1434.0      Alaska
    2       7259.0     Arizona
    3       2280.0    Arkansas
    4     109008.0  California
```

## Exercise: Subsetting rows

A large part of data science is about finding which bits of your dataset are interesting. One of the simplest techniques for this is to find a subset of rows that match some criteria. This is sometimes known as filtering rows or selecting rows.

There are many ways to subset a DataFrame, perhaps the most common is to use relational operators to return True or False for each row, then pass that inside square brackets.

```python
dogs[dogs["height_cm"] > 60]
dogs[dogs["color"] == "tan"]
```

You can filter for multiple conditions at once by using the "bitwise and" operator, &.

```python
dogs[(dogs["height_cm"] > 60) & (dogs["color"] == "tan")]
```

homelessness is available and pandas is loaded as pd.

    Filter homelessness for cases where the number of individuals is greater than ten thousand, assigning to ind_gt_10k. View the printed result.

    Filter homelessness for cases where the USA Census region is "Mountain", assigning to mountain_reg. View the printed result.

    Filter homelessness for cases where the number of family_members is less than one thousand and the region is "Pacific", assigning to fam_lt_1k_pac. View the printed result.

## Solution

```python
# Filter for rows where individuals is greater than 10000
ind_gt_10k = homelessness[homelessness["individuals"] > 10000]

# See the result
print(ind_gt_10k)

# Results
                region       state  individuals  family_members  state_pop
4              Pacific  California     109008.0         20964.0   39461588
9       South Atlantic     Florida      21443.0          9587.0   21244317
32        Mid-Atlantic    New York      39827.0         52070.0   19530351
37             Pacific      Oregon      11139.0          3337.0    4181886
43  West South Central       Texas      19199.0          6111.0   28628666
47             Pacific  Washington      16424.0          5880.0    7523869


# Filter for rows where region is Mountain
mountain_reg = homelessness[homelessness["region"] == "Mountain"]

# See the result
print(mountain_reg)

# Results
      region       state  individuals  family_members  state_pop
2   Mountain     Arizona       7259.0          2606.0    7158024
5   Mountain    Colorado       7607.0          3250.0    5691287
12  Mountain       Idaho       1297.0           715.0    1750536
26  Mountain     Montana        983.0           422.0    1060665
28  Mountain      Nevada       7058.0           486.0    3027341
31  Mountain  New Mexico       1949.0           602.0    2092741
44  Mountain        Utah       1904.0           972.0    3153550
50  Mountain     Wyoming        434.0           205.0     577601


# Filter for rows where family_members is less than 1000 
# and region is Pacific
fam_lt_1k_pac = homelessness[(homelessness["family_members"] < 1000) & (homelessness["region"] == "Pacific")]

# See the result
print(fam_lt_1k_pac)

# Results
    region   state  individuals  family_members  state_pop
1  Pacific  Alaska       1434.0           582.0     735139
```

## Exercise: Subsetting rows by categorical variables

Subsetting data based on a categorical variable often involves using the or operator (|) to select rows from multiple categories. This can get tedious when you want all states in one of three different regions, for example. Instead, use the .isin() method, which will allow you to tackle this problem by writing one condition instead of three separate ones.

```python
colors = ["brown", "black", "tan"]
condition = dogs["color"].isin(colors)
dogs[condition]
```

homelessness is available and pandas is loaded as pd.

    Filter homelessness for cases where the USA census state is in the list of Mojave states, canu, assigning to mojave_homelessness. View the printed result.

## Solution

```python
# The Mojave Desert states
canu = ["California", "Arizona", "Nevada", "Utah"]

# Filter for rows in the Mojave Desert states
mojave_homelessness = homelessness[homelessness["state"].isin(canu)]

# See the result
print(mojave_homelessness)

# Result
      region       state  individuals  family_members  state_pop
2   Mountain     Arizona       7259.0          2606.0    7158024
4    Pacific  California     109008.0         20964.0   39461588
28  Mountain      Nevada       7058.0           486.0    3027341
44  Mountain        Utah       1904.0           972.0    3153550
```

<img width="1152" height="542" alt="image" src="https://github.com/user-attachments/assets/6f233511-b882-4efe-af7e-71619a46caa7" />

<img width="1166" height="498" alt="image" src="https://github.com/user-attachments/assets/f05e2e85-41d1-49bc-8376-a6422394e413" />

<img width="1173" height="459" alt="image" src="https://github.com/user-attachments/assets/8a9d7355-1157-478f-b20f-ebf646ec67a3" />


## Exercise: Adding new columns

You aren't stuck with just the data you are given. Instead, you can add new columns to a DataFrame. This has many names, such as transforming, mutating, and feature engineering.

You can create new columns from scratch, but it is also common to derive them from other columns, for example, by adding columns together or by changing their units.

homelessness is a DataFrame containing estimates of homelessness in each U.S. state in 2018. The individual column is the number of homeless individuals not part of a family with children. The family_members column is the number of homeless individuals part of a family with children. The state_pop column is the state's total population.

homelessness is available and pandas is loaded as pd.

    Add a new column to homelessness, named total, containing the sum of the individuals and family_members columns.

    Add another column to homelessness, named p_homeless, containing the proportion of the total homeless population to the total population in each state state_pop.

## Solution

```python
# Add total col as sum of individuals and family_members
homelessness["total"] = homelessness["individuals"] + homelessness["family_members"]

# Add p_homeless col as proportion of total homeless people to the state population
homelessness["p_homeless"] = homelessness["total"] / homelessness["state_pop"]

# See the result
print(homelessness)

# Result
                region                 state  individuals  family_members  state_pop     total  p_homeless
0   East South Central               Alabama       2570.0           864.0    4887681    3434.0   7.026e-04
1              Pacific                Alaska       1434.0           582.0     735139    2016.0   2.742e-03
2             Mountain               Arizona       7259.0          2606.0    7158024    9865.0   1.378e-03
```

## Exercise: Combo-attack!

You've seen the four most common types of data manipulation: sorting rows, subsetting columns, subsetting rows, and adding new columns. In a real-life data analysis, you can mix and match these four manipulations to answer a multitude of questions.

In this exercise, you'll answer the question, "Which state has the highest number of homeless individuals per 10,000 people in the state?" Combine your new pandas skills to find out.

    Add a column to homelessness, indiv_per_10k, containing the number of homeless individuals per ten thousand people in each state, using state_pop for state population.

    Subset rows where indiv_per_10k is higher than 20, assigning to high_homelessness.

    Sort high_homelessness by descending indiv_per_10k, assigning to high_homelessness_srt.

    Select only the state and indiv_per_10k columns of high_homelessness_srt and save as result. Look at the result.

## Solution

```python
# Create indiv_per_10k col as homeless individuals per 10k state pop
homelessness["indiv_per_10k"] = 10000 * homelessness["individuals"] / homelessness["state_pop"] 

# Subset rows for indiv_per_10k greater than 20
high_homelessness = homelessness[homelessness["indiv_per_10k"] > 20]

# Sort high_homelessness by descending indiv_per_10k
high_homelessness_srt = high_homelessness.sort_values("indiv_per_10k", ascending=False)

# From high_homelessness_srt, select the state and indiv_per_10k cols
result = high_homelessness_srt[["state", "indiv_per_10k"]]

# See the result
print(result)

# Result
                   state  indiv_per_10k
8   District of Columbia         53.738
11                Hawaii         29.079
4             California         27.624
37                Oregon         26.636
28                Nevada         23.314
47            Washington         21.829
32              New York         20.392
```

# Aggregating DataFrames

One of the most common summary statistics for numeric data is the mean, which is one way of telling you where the "center" of your data is. You can calculate the mean of a column by selecting the column with square brackets and calling dot-mean. There are lots of other summary statistics that you can compute on columns, like median and mode, minimum and maximum, and variance and standard deviation. You can also take sums and calculate quantiles.

<img width="1174" height="339" alt="image" src="https://github.com/user-attachments/assets/6587e08e-64d0-4d48-8ae9-e32416e6fcfd" />

You can also get summary statistics for date columns. For example, we can find the oldest dog's date of birth by taking the minimum of the date of birth column. Similarly, we can take the maximum to see that the youngest dog was born in 2018. 

<img width="1158" height="501" alt="image" src="https://github.com/user-attachments/assets/a22d50ae-3c7f-4ec6-9b39-54d22f94582d" />

The aggregate, or agg, method allows you to compute custom summary statistics. Here, we create a function called pct30 that computes the thirtieth percentile of a DataFrame column. Don't worry if this code doesn't make sense to you -- just know that the function takes in a column and spits out the column's thirtieth percentile. Now we can subset the weight column and call dot-agg, passing in the name of our function, pct30. It gives us the thirtieth percentile of the dogs' weights. 

<img width="1170" height="358" alt="image" src="https://github.com/user-attachments/assets/c5a1b479-931c-4d63-acb3-90e19fc3a721" />

agg can also be used on more than one column. By selecting the weight and height columns before calling agg, we get the thirtieth percentile for both columns. 

<img width="1157" height="303" alt="image" src="https://github.com/user-attachments/assets/b1f014ef-9434-4dbe-8c0a-8b544e7d1e3e" />

We can also use agg to get multiple summary statistics at once. Here's another function that computes the fortieth percentile called pct40. We can pass a list of functions into agg, in this case, pct30 and pct40, which will return the thirtieth and fortieth percentiles of the dogs' weights. 

<img width="1159" height="428" alt="image" src="https://github.com/user-attachments/assets/c2d0143a-641e-48d3-88fd-5b3ac3af1974" />

pandas also has methods for computing cumulative statistics, for example, the cumulative sum. Calling cumsum on a column returns not just one number, but a number for each row of the DataFrame. The first number returned, or the number in the zeroth index, is the first dog's weight. The next number is the sum of the first and second dogs' weights. The third number is the sum of the first, second, and third dogs' weights, and so on. The last number is the sum of all the dogs' weights. 

<img width="1156" height="487" alt="image" src="https://github.com/user-attachments/assets/e5748d5b-258b-40b9-b025-fb6f472f120a" />

pandas also has methods for other cumulative statistics, such as the cumulative maximum, cumulative minimum, and the cumulative product. These all return an entire column of a DataFrame, rather than a single number. 

<img width="1048" height="236" alt="image" src="https://github.com/user-attachments/assets/379e4544-047e-498c-8ff5-eb7caac1daf4" />

In this chapter, you'll be working with data on Walmart stores, which is a chain of department stores in the US. The dataset contains weekly sales in US dollars in various stores. Each store has an ID number and a specific store type. The sales are also separated by department ID. Along with weekly sales, there is information about whether it was a holiday week or not, the average temperature during the week in that location, the average fuel price in dollars per liter that week, and the national unemployment rate that week. 

<img width="1146" height="425" alt="image" src="https://github.com/user-attachments/assets/f8faaaf2-e803-4afd-ba18-a00d22ea655c" />


## Exercise: Mean and median

Summary statistics are exactly what they sound like - they summarize many numbers in one statistic. For example, mean, median, minimum, maximum, and standard deviation are summary statistics. Calculating summary statistics allows you to get a better sense of your data, even if there's a lot of it.

sales is available and pandas is loaded as pd.

    
    Explore your new DataFrame first by printing the first few rows of the sales DataFrame.
    Print information about the columns in sales.
    Print the mean of the weekly_sales column.
    Print the median of the weekly_sales column.

## Solution

```python
# Print the head of the sales DataFrame
print(sales.head())

# Print the info about the sales DataFrame
print(sales.info())

# Print the mean of weekly_sales
print(sales["weekly_sales"].mean())

# Print the median of weekly_sales
print(sales["weekly_sales"].median())

# Results
   store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0      1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
1      1    A           1 2010-03-05      21827.90       False          8.056                 0.693         8.106
2      1    A           1 2010-04-02      57258.43       False         16.817                 0.718         7.808
3      1    A           1 2010-05-07      17413.94       False         22.528                 0.749         7.808
4      1    A           1 2010-06-04      17558.09       False         27.050                 0.715         7.808
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 10774 entries, 0 to 10773
Data columns (total 9 columns):
 #   Column                Non-Null Count  Dtype         
---  ------                --------------  -----         
 0   store                 10774 non-null  int64         
 1   type                  10774 non-null  object        
 2   department            10774 non-null  int32         
 3   date                  10774 non-null  datetime64[ns]
 4   weekly_sales          10774 non-null  float64       
 5   is_holiday            10774 non-null  bool          
 6   temperature_c         10774 non-null  float64       
 7   fuel_price_usd_per_l  10774 non-null  float64       
 8   unemployment          10774 non-null  float64       
dtypes: bool(1), datetime64[ns](1), float64(4), int32(1), int64(1), object(1)
memory usage: 641.9+ KB
None
23843.95014850566
12049.064999999999
```

## Exercise: Summarizing dates

Summary statistics can also be calculated on date columns that have values with the data type datetime64. Some summary statistics — like mean — don't make a ton of sense on dates, but others are super helpful, for example, minimum and maximum, which allow you to see what time range your data covers.

sales is available and pandas is loaded as pd.
    
    Print the maximum of the date column.
    Print the minimum of the date column.

## Solution

```python
# Print the maximum of the date column
print(sales["date"].max())

# Print the minimum of the date column
print(sales["date"].min())

# Results
2012-10-26 00:00:00
2010-02-05 00:00:00
```

## Exercise: Efficient summaries

While pandas and NumPy have tons of functions, sometimes, you may need a different function to summarize your data.

The .agg() method allows you to apply your own custom functions to a DataFrame, as well as apply functions to more than one column of a DataFrame at once, making your aggregations super-efficient. For example, 

```python
df['column'].agg(function)
```

In the custom function for this exercise, "IQR" is short for inter-quartile range, which is the 75th percentile minus the 25th percentile. It's an alternative to standard deviation that is helpful if your data contains outliers.

sales is available and pandas is loaded as pd.

    Use the custom iqr function defined for you along with .agg() to print the IQR of the temperature_c column of sales.

    Update the column selection to use the custom iqr function with .agg() to print the IQR of temperature_c, fuel_price_usd_per_l, and unemployment, in that order.

    Update the aggregation functions called by .agg(): include iqr and "median" in that order.


## Solution

```python
# A custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)
    
# Print IQR of the temperature_c column
print(sales["temperature_c"].agg(iqr))

#Results
16.583333333333336
--------------

# A custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Update to print IQR of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", "fuel_price_usd_per_l", "unemployment"]].agg(iqr))

#Results
temperature_c           16.583
fuel_price_usd_per_l     0.073
unemployment             0.565
dtype: float64
--------------

# Create a custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Update to print IQR and median of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", "fuel_price_usd_per_l", "unemployment"]].agg([iqr, "median"]))

#Results
        temperature_c  fuel_price_usd_per_l  unemployment
iqr            16.583                 0.073         0.565
median         16.967                 0.743         8.099
```

## Exercise: Cumulative statistics

Cumulative statistics can also be helpful in tracking summary statistics over time. In this exercise, you'll calculate the cumulative sum and cumulative max of a department's weekly sales, which will allow you to identify what the total sales were so far as well as what the highest weekly sales were so far.

A DataFrame called sales_1_1 has been created for you, which contains the sales data for department 1 of store 1. pandas is loaded as pd.

    
    Sort the rows of sales_1_1 by the date column in ascending order.
    Get the cumulative sum of weekly_sales and add it as a new column of sales_1_1 called cum_weekly_sales.
    Get the cumulative maximum of weekly_sales, and add it as a column called cum_max_sales.
    Print the date, weekly_sales, cum_weekly_sales, and cum_max_sales columns.

## Solution

```python
# Sort sales_1_1 by date
sales_1_1 = sales_1_1.sort_values(by='date', ascending=True)

# Get the cumulative sum of weekly_sales, add as cum_weekly_sales col
sales_1_1["cum_weekly_sales"] = sales_1_1["weekly_sales"].cumsum()

# Get the cumulative max of weekly_sales, add as cum_max_sales col
sales_1_1["cum_max_sales"] = sales_1_1["weekly_sales"].cummax()

# See the columns you calculated
print(sales_1_1[["date", "weekly_sales", "cum_weekly_sales", "cum_max_sales"]])

#Results
             date  weekly_sales  cum_weekly_sales  cum_max_sales
    0  2010-02-05      24924.50          24924.50       24924.50
    1  2010-03-05      21827.90          46752.40       24924.50
    2  2010-04-02      57258.43         104010.83       57258.43
    3  2010-05-07      17413.94         121424.77       57258.43
    4  2010-06-04      17558.09         138982.86       57258.43
    5  2010-07-02      16333.14         155316.00       57258.43
    6  2010-08-06      17508.41         172824.41       57258.43
    7  2010-09-03      16241.78         189066.19       57258.43
    8  2010-10-01      20094.19         209160.38       57258.43
    9  2010-11-05      34238.88         243399.26       57258.43
    10 2010-12-03      22517.56         265916.82       57258.43
    11 2011-01-07      15984.24         281901.06       57258.43
```

Here's a DataFrame that contains vet visits. The vet's office wants to know how many dogs of each breed have visited their office. However, some dogs have been to the vet more than once, like Max and Stella, so we can't just count the number of each breed in the breed column. 

<img width="1136" height="502" alt="image" src="https://github.com/user-attachments/assets/59f2f506-257e-4f36-921a-352d35bd4014" />

Let's try to fix this by removing rows that contain a dog name already listed earlier in the dataset, or in other words; we'll extract a dog with each name from the dataset once. We can do this using the drop_duplicates method. It takes an argument, subset, which is the column we want to find our duplicates based on - in this case, we want all the unique names. Now we have a list of dogs where each one appears once. We have Max the Chow Chow, but where did Max the Labrador go? Because we have two different dogs with the same name, we'll need to consider more than just name when dropping duplicates. 

<img width="1154" height="529" alt="image" src="https://github.com/user-attachments/assets/be222721-3483-41ea-94ff-9ff3d05bdef0" />

Since Max and Max are different breeds, we can drop the rows with pairs of name and breed listed earlier in the dataset. To base our duplicate dropping on multiple columns, we can pass a list of column names to the subset argument, in this case, name and breed. Now both Maxes have been included, and we can start counting.

<img width="1152" height="543" alt="image" src="https://github.com/user-attachments/assets/ed019f02-541e-46f5-a6ef-800bceed7b11" />

To count the dogs of each breed, we'll subset the breed column and use the value_counts method. We can also use the sort argument to get the breeds with the biggest counts on top. 

<img width="1162" height="420" alt="image" src="https://github.com/user-attachments/assets/daba6310-2f79-41cb-a5c9-25e4fe1c8373" />

The normalize argument can be used to turn the counts into proportions of the total. 25% of the dogs that go to this vet are Labradors. 

<img width="1141" height="453" alt="image" src="https://github.com/user-attachments/assets/f5142c39-f1d5-4d14-801f-8e54cac22afc" />

## Exercise: Dropping duplicates

Removing duplicates is an essential skill to get accurate counts because often, you don't want to count the same thing multiple times. In this exercise, you'll create some new DataFrames using unique values from sales.

sales is available and pandas is imported as pd.

    
    Remove rows of sales with duplicate pairs of store and type and save as store_types and print the head.
    Remove rows of sales with duplicate pairs of store and department and save as store_depts and print the head.
    Subset the rows that are holiday weeks using the is_holiday column, and drop the duplicate dates, saving as holiday_dates.
    Select the date column of holiday_dates, and print.

## Solution

```python
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset=["store", "type"])
print(store_types.head())

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=["store", "department"])
print(store_depts.head())

# Subset the rows where is_holiday is True and drop duplicate dates
holiday_dates = sales[sales["is_holiday"]].drop_duplicates(subset="date")

# Print date col of holiday_dates
print(holiday_dates["date"])

#Result
      store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0         1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
901       2    A           1 2010-02-05      35034.06       False          4.550                 0.679         8.324
1798      4    A           1 2010-02-05      38724.42       False          6.533                 0.686         8.623
2699      6    A           1 2010-02-05      25619.00       False          4.683                 0.679         7.259
3593     10    B           1 2010-02-05      40212.84       False         12.411                 0.782         9.765
    store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0       1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
12      1    A           2 2010-02-05      50605.27       False          5.728                 0.679         8.106
24      1    A           3 2010-02-05      13740.12       False          5.728                 0.679         8.106
36      1    A           4 2010-02-05      39954.04       False          5.728                 0.679         8.106
48      1    A           5 2010-02-05      32229.38       False          5.728                 0.679         8.106
498    2010-09-10
691    2011-11-25
2315   2010-02-12
6735   2012-09-07
6810   2010-12-31
6815   2012-02-10
6820   2011-09-09
Name: date, dtype: datetime64[ns]
```

## Exercise: Counting categorical variables

Counting is a great way to get an overview of your data and to spot curiosities that you might not notice otherwise. In this exercise, you'll count the number of each type of store and the number of each department number using the DataFrames you created in the previous exercise:

```python
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset=["store", "type"])

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=["store", "department"])
```

The store_types and store_depts DataFrames you created in the last exercise are available, and pandas is imported as pd.

    
    Count the number of stores of each store type in store_types.
    Count the proportion of stores of each store type in store_types.
    Count the number of stores of each department in store_depts, sorting the counts in descending order.
    Count the proportion of stores of each department in store_depts, sorting the proportions in descending order.

## Solution

```python
# Count the number of stores of each type
store_counts = store_types["type"].value_counts()
print(store_counts)

# Get the proportion of stores of each type
store_props = store_types["type"].value_counts(normalize=True)
print(store_props)

# Count the number of stores of each department and sort
dept_counts_sorted = store_depts["department"].value_counts(sort=True)
print(dept_counts_sorted)

# Get the proportion of stores of each department and sort
dept_props_sorted = store_depts["department"].value_counts(sort=True, normalize=True)
print(dept_props_sorted)

#Result
<script.py> output:
    type
    A    11
    B     1
    Name: count, dtype: int64
    type
    A    0.917
    B    0.083
    Name: proportion, dtype: float64
    department
    1    12
    Name: count, dtype: int64
    department
    1    1.0
    Name: proportion, dtype: float64
```

While computing summary statistics of entire columns may be useful, you can gain many insights from summaries of individual groups. For example, does one color of dog weigh more than another on average? Are female dogs taller than males? You can already answer these questions with what you've learned so far! We can subset the dogs into groups based on their color, and take the mean of each. But that's a lot of work, and the duplicated code means you can easily introduce copy and paste bugs. 

<img width="1154" height="511" alt="image" src="https://github.com/user-attachments/assets/36614034-e9e7-4db5-9cf2-f4ccac3d67a4" />

That's where the groupby method comes in. We can group by the color variable, select the weight column, and take the mean. This will give us the mean weight for each dog color. This was just one line of code compared to the five we had to write before to get the same results. 

<img width="1154" height="447" alt="image" src="https://github.com/user-attachments/assets/7b59ff04-11e8-4681-b264-8412f7c67248" />

Just like with ungrouped summary statistics, we can use the agg method to get multiple statistics. Here, we pass a list of functions into agg after grouping by color. This gives us the minimum, maximum, and sum of the different colored dogs' weights. 

<img width="1156" height="460" alt="image" src="https://github.com/user-attachments/assets/b49374fd-cb5f-426e-866c-3404966cd2d3" />

You can also group by multiple columns and calculate summary statistics. Here, we group by color and breed, select the weight column and take the mean. This gives us the mean weight of each breed of each color. 

<img width="1131" height="532" alt="image" src="https://github.com/user-attachments/assets/f206dff9-750a-4283-827b-8022f09b5944" />

You can also group by multiple columns and aggregate by multiple columns. 

<img width="1143" height="530" alt="image" src="https://github.com/user-attachments/assets/6a58fa46-68bf-419d-aee4-f1109b4c97c9" />




