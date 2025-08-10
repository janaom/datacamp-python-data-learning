# Data Manipulation with pandas

pandas is the world's most popular Python library, used for everything from data manipulation to data analysis. In this course, you'll learn how to manipulate DataFrames, as you extract, filter, and transform real-world datasets for analysis. Using pandas you’ll explore all the core data science concepts. Using real-world data, including Walmart sales figures and global temperature time series, you’ll learn how to import, clean, calculate statistics, and create visualizations—using pandas to add to the power of Python!

---------------

✅ [Transforming DataFrames](https://github.com/janaom/datacamp-python-data-learning/tree/main/data-manipulation-with-pandas#transforming-dataframes)

✅ [Aggregating DataFrames](https://github.com/janaom/datacamp-python-data-learning/blob/main/data-manipulation-with-pandas/README.md#aggregating-dataframes)

✅ [Slicing and Indexing DataFrames](https://github.com/janaom/datacamp-python-data-learning/tree/main/data-manipulation-with-pandas#slicing-and-indexing-dataframes)

✅ [Creating and Visualizing DataFrames](https://github.com/janaom/datacamp-python-data-learning/blob/main/data-manipulation-with-pandas/README.md#creating-and-visualizing-dataframes)

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

## Exercise: What percent of sales occurred at each store type?

While .groupby() is useful, you can calculate grouped summary statistics without it.

Walmart distinguishes three types of stores: "supercenters," "discount stores," and "neighborhood markets," encoded in this dataset as type "A," "B," and "C." In this exercise, you'll calculate the total sales made at each store type, without using .groupby(). You can then use these numbers to see what proportion of Walmart's total sales were made at each type.

sales is available and pandas is imported as pd.

    
    Calculate the total weekly_sales over the whole dataset.
    Subset for type "A" stores, and calculate their total weekly sales.
    Do the same for type "B" and type "C" stores.
    Combine the A/B/C results into a list, and divide by sales_all to get the proportion of sales by type.

## Solution

```python
# Calc total weekly sales
sales_all = sales["weekly_sales"].sum()

# Subset for type A stores, calc total weekly sales
sales_A = sales[sales["type"] == "A"]["weekly_sales"].sum()

# Subset for type B stores, calc total weekly sales
sales_B = sales[sales["type"] == "B"]["weekly_sales"].sum()

# Subset for type C stores, calc total weekly sales
sales_C = sales[sales["type"] == "C"]["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = [sales_A, sales_B, sales_C] / sales_all
print(sales_propn_by_type)

# Results
[0.9097747 0.0902253 0.       ]
```

## Exercise: Calculations with .groupby()

The .groupby() method makes life much easier. In this exercise, you'll perform the same calculations as last time, except you'll use the .groupby() method. You'll also perform calculations on data grouped by two variables to see if sales differ by store type depending on if it's a holiday week or not.

sales is available and pandas is loaded as pd.

    
    Group sales by "type", take the sum of "weekly_sales", and store as sales_by_type.
    Calculate the proportion of sales at each store type by dividing by the sum of sales_by_type. Assign to sales_propn_by_type.
    Group sales by "type" and "is_holiday", take the sum of weekly_sales, and store as sales_by_type_is_holiday.

## Solution

```python
# Group by type; calc total weekly sales
sales_by_type = sales.groupby("type")["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = sales_by_type / sum(sales_by_type)
print(sales_propn_by_type)

#Results
type
A    0.91
B    0.09
Name: weekly_sales, dtype: float64

------------------

# From previous step
sales_by_type = sales.groupby("type")["weekly_sales"].sum()

# Group by type and is_holiday; calc total weekly sales
sales_by_type_is_holiday = sales.groupby(["type", "is_holiday"])["weekly_sales"].sum()
print(sales_by_type_is_holiday)

#Results
type  is_holiday
A     False         2.337e+08
      True          2.360e+04
B     False         2.318e+07
      True          1.621e+03
Name: weekly_sales, dtype: float64

```

## Exercise: Multiple grouped summaries

Earlier in this chapter, you saw that the .agg() method is useful to compute multiple statistics on multiple variables. It also works with grouped data. You can use built-in functions like min, max, mean, and median.

sales is available and pandas is imported as pd.

    
    Get the min, max, mean, and median of weekly_sales for each store type using .groupby() and .agg(). Store this as sales_stats.
    Get the min, max, mean, and median of unemployment and fuel_price_usd_per_l for each store type. Store this as unemp_fuel_stats.

## Solution

```python
# For each store type, aggregate weekly_sales: get min, max, mean, and median
sales_stats = sales.groupby("type")["weekly_sales"].agg(["min", "max", "mean", "median"])

# Print sales_stats
print(sales_stats)

# For each store type, aggregate unemployment and fuel_price_usd_per_l: get min, max, mean, and median
unemp_fuel_stats = sales.groupby("type")[["unemployment", "fuel_price_usd_per_l"]].agg(["min", "max", "mean", "median"])

# Print unemp_fuel_stats
print(unemp_fuel_stats)

#Results
         min        max       mean    median
type                                        
A    -1098.0  293966.05  23674.667  11943.92
B     -798.0  232558.51  25696.678  13336.08
     unemployment                      fuel_price_usd_per_l                     
              min    max   mean median                  min    max   mean median
type                                                                            
A           3.879  8.992  7.973  8.067                0.664  1.107  0.745  0.735
B           7.170  9.765  9.279  9.199                0.760  1.108  0.806  0.803
```

Pivot tables are another way of calculating grouped summary statistics. If you've ever used a spreadsheet, chances are you've used a pivot table. Let's see how to create pivot tables in pandas. 
In the last lesson, we grouped the dogs by color and calculated their mean weights. We can do the same thing using the pivot_table method. The "values" argument is the column that you want to summarize, and the index column is the column that you want to group by. By default, pivot_table takes the mean value for each group. 

<img width="1159" height="487" alt="image" src="https://github.com/user-attachments/assets/e2e9d6d2-9c13-49b7-9151-76ad86135898" />

If we want a different summary statistic, we can use the aggfunc argument and pass it a function. Here, we take the median for each dog color. 

<img width="1153" height="450" alt="image" src="https://github.com/user-attachments/assets/bd5744eb-c260-4a25-aa32-5f2e5ac96f20" />

To get multiple summary statistics at a time, we can pass a list of functions to the aggfunc argument. Here, we get the mean and median for each dog color. 

<img width="1147" height="499" alt="image" src="https://github.com/user-attachments/assets/52271c12-f857-4c66-9ef6-085a48ec396e" />

You also previously computed the mean weight grouped by two variables: color and breed. We can also do this using the pivot_table method. To group by two variables, we can pass a second variable name into the columns argument. While the result looks a little different than what we had before, it contains the same numbers. There are NaNs, or missing values, because there are no black Chihuahuas or gray Labradors in our dataset, for example. 

<img width="1137" height="484" alt="image" src="https://github.com/user-attachments/assets/bc7d3e2c-4211-4d6b-b847-4fed91b38d71" />

Instead of having lots of missing values in our pivot table, we can have them filled in using the fill_value argument. Here, all of the NaNs get filled in with zeros. 

<img width="1140" height="445" alt="image" src="https://github.com/user-attachments/assets/e810aee3-b7f3-4747-bc1a-ea5a3e4ed9c4" />

If we set the margins argument to True, the last row and last column of the pivot table contain the mean of all the values in the column or row, not including the missing values that were filled in with Os. For example, in the last row of the Labrador column, we can see that the mean weight of the Labradors is 26 kilograms. In the last column of the Brown row, the mean weight of the Brown dogs is 24 kilograms. The value in the bottom right, in the last row and last column, is the mean weight of all the dogs in the dataset. Using margins equals True allows us to see a summary statistic for multiple levels of the dataset: the entire dataset, grouped by one variable, by another variable, and by two variables. 

<img width="1133" height="520" alt="image" src="https://github.com/user-attachments/assets/a1210330-e89a-402a-abaf-608f5fe0e4d7" />


## Exercise: Pivoting on one variable

Pivot tables are the standard way of aggregating data in spreadsheets.

In pandas, pivot tables are essentially another way of performing grouped calculations. That is, the .pivot_table() method is an alternative to .groupby().

In this exercise, you'll perform calculations using .pivot_table() to replicate the calculations you performed in the last lesson using .groupby().

sales is available and pandas is imported as pd.


    Get the mean weekly_sales by type using .pivot_table() and store as mean_sales_by_type.
    Get the mean and median of weekly_sales by type using .pivot_table() and store as mean_med_sales_by_type.
    Get the mean of weekly_sales by type and is_holiday using .pivot_table() and store as mean_sales_by_type_holiday.

## Solution

```python
# Pivot for mean weekly_sales for each store type
mean_sales_by_type = sales.pivot_table(values = "weekly_sales", index = "type")

# Print mean_sales_by_type
print(mean_sales_by_type)

#Results
      weekly_sales
type              
A        23674.667
B        25696.678

------------------

# Pivot for mean and median weekly_sales for each store type
mean_med_sales_by_type = sales.pivot_table(values = "weekly_sales", index = "type", aggfunc = ["mean", "median"])

# Print mean_med_sales_by_type
print(mean_med_sales_by_type)

#Results
             mean       median
     weekly_sales weekly_sales
type                          
A       23674.667     11943.92
B       25696.678     13336.08

-----------------------

# Pivot for mean weekly_sales by store type and holiday 
mean_sales_by_type_holiday = sales.pivot_table(values = "weekly_sales", index = "type", columns = "is_holiday")

# Print mean_sales_by_type_holiday
print(mean_sales_by_type_holiday)

#Results
<script.py> output:
    is_holiday      False    True 
    type                          
    A           23768.584  590.045
    B           25751.981  810.705
```

## Exercise: Fill in missing values and sum values with pivot tables

The .pivot_table() method has several useful arguments, including fill_value and margins.

- fill_value replaces missing values with a real value (known as imputation). What to replace missing values with is a topic big enough to have its own course (Dealing with Missing Data in Python), but the simplest thing to do is to substitute a dummy value.
- margins is a shortcut for when you pivoted by two variables, but also wanted to pivot by each of those variables separately: it gives the row and column totals of the pivot table contents.

In this exercise, you'll practice using these arguments to up your pivot table skills, which will help you crunch numbers more efficiently!

sales is available and pandas is imported as pd.

    Print the mean weekly_sales by department and type, filling in any missing values with 0.
    Print the mean weekly_sales by department and type, filling in any missing values with 0 and summing all rows and columns.

## Solution

```python
# Print mean weekly_sales by department and type; fill missing values with 0
print(sales.pivot_table(values = "weekly_sales", index = "type", columns = "department", fill_value=0))

#Results
department         1           2          3          4          5   ...          95         96         97         98       99
type                                                                ...                                                      
A           30961.725   67600.159  17160.003  44285.399  34821.011  ...  123933.787  21367.043  28471.267  12875.423  379.124
B           44050.627  112958.527  30580.655  51219.654  63236.875  ...   77082.102   9528.538   5828.873    217.428    0.000

[2 rows x 80 columns]

---------------

# Print the mean weekly_sales by department and type; fill missing values with 0s; sum all rows and cols
print(sales.pivot_table(values="weekly_sales", index="department", columns="type", fill_value=0, margins=True))

#Results
type                A           B        All
department                                  
1           30961.725   44050.627  32052.467
2           67600.159  112958.527  71380.023
3           17160.003   30580.655  18278.391
4           44285.399   51219.654  44863.254
5           34821.011   63236.875  37189.000
...               ...         ...        ...
96          21367.043    9528.538  20337.608
97          28471.267    5828.873  26584.401
98          12875.423     217.428  11820.590
99            379.124       0.000    379.124
All         23674.667   25696.678  23843.950

[81 rows x 3 columns]
```

# Slicing and Indexing DataFrames

Here's the dog dataset again. 

<img width="1139" height="490" alt="image" src="https://github.com/user-attachments/assets/f4bde2dd-0a46-48b0-b682-757cc7acaa79" />

Recall that dot-columns contains an Index object of column names, and dot-index contains an Index object of row numbers. 

<img width="1140" height="388" alt="image" src="https://github.com/user-attachments/assets/68a2ed99-52f6-46a7-b5a7-c7b737ae303f" />

You can move a column from the body of the DataFrame to the index. This is called "setting an index," and it uses the set_index method. Notice that the output has changed slightly; in particular, a quick visual clue that name is now in the index is that the index values are left-aligned rather than right-aligned. 

<img width="1147" height="538" alt="image" src="https://github.com/user-attachments/assets/5c550ec5-c3f2-43e7-b389-29257ba1965a" />

To undo what you just did, you can reset the index - that is, you remove it. This is done via reset_index. 

<img width="1146" height="480" alt="image" src="https://github.com/user-attachments/assets/ff3eeb0c-c4f8-40b4-a595-6d93be4185de" />

reset_index has a drop argument that allows you to discard an index. Here, setting drop to True entirely removes the dog names. 

<img width="1145" height="496" alt="image" src="https://github.com/user-attachments/assets/bfd1683d-9aed-4442-bd19-3434da57c8ee" />

You may be wondering why you should bother with indexes. The answer is that it makes subsetting code cleaner. Consider this example of subsetting for the rows where the dog is called Bella or Stella. It's a fairly tricky line of code for such a simple task. Now, look at the equivalent when the names are in the index. DataFrames have a subsetting method called "loc," which filters on index values. Here you simply pass the dog names to loc as a list. Much easier! 

<img width="1132" height="536" alt="image" src="https://github.com/user-attachments/assets/64a1c015-32b1-42c9-8db3-392229e5d995" />

The values in the index don't need to be unique. Here, there are two Labradors in the index. 

<img width="1130" height="538" alt="image" src="https://github.com/user-attachments/assets/d760c4a5-7a5f-4115-be3d-2208c66dcd4d" />

Now, if you subset on "Labrador" using loc, all the Labrador data is returned. 

<img width="1157" height="333" alt="image" src="https://github.com/user-attachments/assets/970dd517-90a6-4f4b-86c3-842c80d6f766" />

You can include multiple columns in the index by passing a list of column names to set_index. Here, breed and color are included. These are called multi-level indexes, or hierarchical indexes: the terms are synonymous. There is an implication here that the inner level of index, in this case, color, is nested inside the outer level, breed. 

<img width="1139" height="545" alt="image" src="https://github.com/user-attachments/assets/4648d7f3-bb33-4810-94f8-6314c28cf9b5" />

To take a subset of rows at the outer level index, you pass a list of index values to loc. Here, the list contains Labrador and Chihuahua, and the resulting subset contains all dogs from both breeds. 

<img width="1141" height="372" alt="image" src="https://github.com/user-attachments/assets/4e178587-10ba-4f0b-b826-22b3daf09acf" />

To subset on inner levels, you need to pass a list of tuples. Here, the first tuple specifies Labrador at the outer level and Brown at the inner level. The resulting rows have to match all conditions from a tuple. For example, the black Labrador wasn't returned because the brown condition wasn't matched. 

<img width="1144" height="337" alt="image" src="https://github.com/user-attachments/assets/f9f937a4-ca64-40b1-9edd-4d5cb85f883a" />

In chapter 1, you saw how to sort the rows of a DataFrame using sort_values. You can also sort by index values using sort_index. By default, it sorts all index levels from outer to inner, in ascending order. 

<img width="1135" height="522" alt="image" src="https://github.com/user-attachments/assets/095fe42a-199f-4405-b062-b644b5ba389b" />

You can control the sorting by passing lists to the level and ascending arguments. 

<img width="1132" height="521" alt="image" src="https://github.com/user-attachments/assets/654dc1c6-be45-484d-8fc9-52dedcd7bd11" />

Indexes are controversial. Although they simplify subsetting code, there are some downsides. Index values are just data. Storing data in multiple forms makes it harder to think about. There is a concept called "tidy data," where data is stored in tabular form - like a DataFrame. Each row contains a single observation, and each variable is stored in its own column. Indexes violate the last rule since index values don't get their own column. In pandas, the syntax for working with indexes is different from the syntax for working with columns. By using two syntaxes, your code is more complicated, which can result in more bugs. If you decide you don't want to use indexes, that's perfectly reasonable. However, it's useful to know how they work for cases when you need to read other people's code. 


## Exercise: Setting and removing indexes

pandas allows you to designate columns as an index. This enables cleaner code when taking subsets (as well as providing more efficient lookup under some circumstances).

In this chapter, you'll be exploring temperatures, a DataFrame of average temperatures in cities around the world. pandas is loaded as pd.

    
    Look at temperatures.
    Set the index of temperatures to "city", assigning to temperatures_ind.
    Look at temperatures_ind. How is it different from temperatures?
    Reset the index of temperatures_ind, keeping its contents.
    Reset the index of temperatures_ind, dropping its contents.

## Solution

```python
# Look at temperatures
print(temperatures)

# Set the index of temperatures to city
temperatures_ind = temperatures.set_index("city")

# Look at temperatures_ind
print(temperatures_ind)

# Reset the temperatures_ind index, keeping its contents
print(temperatures.reset_index)

# Reset the temperatures_ind index, dropping its contents
print(temperatures.reset_index(drop=True))

##Results
            date     city        country  avg_temp_c
0     2000-01-01  Abidjan  Côte D'Ivoire      27.293
1     2000-02-01  Abidjan  Côte D'Ivoire      27.685
2     2000-03-01  Abidjan  Côte D'Ivoire      29.061
3     2000-04-01  Abidjan  Côte D'Ivoire      28.162
4     2000-05-01  Abidjan  Côte D'Ivoire      27.547
...          ...      ...            ...         ...
16495 2013-05-01     Xian          China      18.979
16496 2013-06-01     Xian          China      23.522
16497 2013-07-01     Xian          China      25.251
16498 2013-08-01     Xian          China      24.528
16499 2013-09-01     Xian          China         NaN

[16500 rows x 4 columns]
              date        country  avg_temp_c
city                                         
Abidjan 2000-01-01  Côte D'Ivoire      27.293
Abidjan 2000-02-01  Côte D'Ivoire      27.685
Abidjan 2000-03-01  Côte D'Ivoire      29.061
Abidjan 2000-04-01  Côte D'Ivoire      28.162
Abidjan 2000-05-01  Côte D'Ivoire      27.547
...            ...            ...         ...
Xian    2013-05-01          China      18.979
Xian    2013-06-01          China      23.522
Xian    2013-07-01          China      25.251
Xian    2013-08-01          China      24.528
Xian    2013-09-01          China         NaN

[16500 rows x 3 columns]
          city       date        country  avg_temp_c
0      Abidjan 2000-01-01  Côte D'Ivoire      27.293
1      Abidjan 2000-02-01  Côte D'Ivoire      27.685
2      Abidjan 2000-03-01  Côte D'Ivoire      29.061
3      Abidjan 2000-04-01  Côte D'Ivoire      28.162
4      Abidjan 2000-05-01  Côte D'Ivoire      27.547
...        ...        ...            ...         ...
16495     Xian 2013-05-01          China      18.979
16496     Xian 2013-06-01          China      23.522
16497     Xian 2013-07-01          China      25.251
16498     Xian 2013-08-01          China      24.528
16499     Xian 2013-09-01          China         NaN

[16500 rows x 4 columns]
            date        country  avg_temp_c
0     2000-01-01  Côte D'Ivoire      27.293
1     2000-02-01  Côte D'Ivoire      27.685
2     2000-03-01  Côte D'Ivoire      29.061
3     2000-04-01  Côte D'Ivoire      28.162
4     2000-05-01  Côte D'Ivoire      27.547
...          ...            ...         ...
16495 2013-05-01          China      18.979
16496 2013-06-01          China      23.522
16497 2013-07-01          China      25.251
16498 2013-08-01          China      24.528
16499 2013-09-01          China         NaN

[16500 rows x 3 columns]
```

## Exercise: Subsetting with .loc[]

The killer feature for indexes is .loc[]: a subsetting method that accepts index values. When you pass it a single argument, it will take a subset of rows.

The code for subsetting using .loc[] can be easier to read than standard square bracket subsetting, which can make your code less burdensome to maintain.

pandas is loaded as pd. temperatures and temperatures_ind are available; the latter is indexed by city.

    
    Create a list called cities that contains "London" and "Paris".
    Use [] subsetting to filter temperatures for rows where the city column takes a value in the cities list.
    Use .loc[] subsetting to filter temperatures_ind for rows where the city is in the cities list.


## Solution

```python
# Make a list of cities to subset on
cities = ["London", "Paris"]

# Subset temperatures using square brackets
print(temperatures[temperatures["city"].isin(cities)])

# Subset temperatures_ind using .loc[]
print(temperatures_ind.loc[cities])

##Results

            date    city         country  avg_temp_c
8910  2000-01-01  London  United Kingdom       4.693
8911  2000-02-01  London  United Kingdom       6.115
8912  2000-03-01  London  United Kingdom       7.422
8913  2000-04-01  London  United Kingdom       8.246
8914  2000-05-01  London  United Kingdom      12.491
...          ...     ...             ...         ...
12040 2013-05-01   Paris          France      11.703
12041 2013-06-01   Paris          France      16.340
12042 2013-07-01   Paris          France      21.186
12043 2013-08-01   Paris          France      19.235
12044 2013-09-01   Paris          France         NaN

[330 rows x 4 columns]
             date         country  avg_temp_c
city                                         
London 2000-01-01  United Kingdom       4.693
London 2000-02-01  United Kingdom       6.115
London 2000-03-01  United Kingdom       7.422
London 2000-04-01  United Kingdom       8.246
London 2000-05-01  United Kingdom      12.491
...           ...             ...         ...
Paris  2013-05-01          France      11.703
Paris  2013-06-01          France      16.340
Paris  2013-07-01          France      21.186
Paris  2013-08-01          France      19.235
Paris  2013-09-01          France         NaN

[330 rows x 3 columns]
```

## Exercise: Setting multi-level indexes

Indexes can also be made out of multiple columns, forming a multi-level index (sometimes called a hierarchical index). There is a trade-off to using these.

The benefit is that multi-level indexes make it more natural to reason about nested categorical variables. For example, in a clinical trial, you might have control and treatment groups. Then each test subject belongs to one or another group, and we can say that a test subject is nested inside the treatment group. Similarly, in the temperature dataset, the city is located in the country, so we can say a city is nested inside the country.

The main downside is that the code for manipulating indexes is different from the code for manipulating columns, so you have to learn two syntaxes and keep track of how your data is represented.

pandas is loaded as pd. temperatures is available.

    
    Set the index of temperatures to the "country" and "city" columns, and assign this to temperatures_ind.
    Specify two country/city pairs to keep: "Brazil"/"Rio De Janeiro" and "Pakistan"/"Lahore", assigning to rows_to_keep.
    Print and subset temperatures_ind for rows_to_keep using .loc[].

## Solution

```python
# Index temperatures by country & city
temperatures_ind = temperatures.set_index(["country", "city"])

# List of tuples: Brazil, Rio De Janeiro & Pakistan, Lahore
rows_to_keep = [("Brazil", "Rio De Janeiro"), ("Pakistan", "Lahore")]

# Subset for rows to keep
print(temperatures_ind.loc[rows_to_keep])

##Results
                              date  avg_temp_c
country  city                                 
Brazil   Rio De Janeiro 2000-01-01      25.974
         Rio De Janeiro 2000-02-01      26.699
         Rio De Janeiro 2000-03-01      26.270
         Rio De Janeiro 2000-04-01      25.750
         Rio De Janeiro 2000-05-01      24.356
...                            ...         ...
Pakistan Lahore         2013-05-01      33.457
         Lahore         2013-06-01      34.456
         Lahore         2013-07-01      33.279
         Lahore         2013-08-01      31.511
         Lahore         2013-09-01         NaN

[330 rows x 2 columns]

<script.py> output:
                                  date  avg_temp_c
    country  city                                 
    Brazil   Rio De Janeiro 2000-01-01      25.974
             Rio De Janeiro 2000-02-01      26.699
             Rio De Janeiro 2000-03-01      26.270
             Rio De Janeiro 2000-04-01      25.750
             Rio De Janeiro 2000-05-01      24.356
    ...                            ...         ...
    Pakistan Lahore         2013-05-01      33.457
             Lahore         2013-06-01      34.456
             Lahore         2013-07-01      33.279
             Lahore         2013-08-01      31.511
             Lahore         2013-09-01         NaN
    
    [330 rows x 2 columns]
```

## Exercise: Sorting by index values

Previously, you changed the order of the rows in a DataFrame by calling .sort_values(). It's also useful to be able to sort by elements in the index. For this, you need to use .sort_index().

pandas is loaded as pd. temperatures_ind has a multi-level index of country and city, and is available.

    
    Sort temperatures_ind by the index values.
    Sort temperatures_ind by the index values at the "city" level.
    Sort temperatures_ind by ascending country then descending city.


## Solution

```python
# Sort temperatures_ind by index values
print(temperatures_ind.sort_index())

# Sort temperatures_ind by index values at the city level
print(temperatures_ind.sort_index(level="city"))

# Sort temperatures_ind by country then descending city
print(temperatures_ind.sort_index(level=["country", "city"], ascending = [True, False]))

##Results
                         date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
                            date  avg_temp_c
country       city                          
Côte D'Ivoire Abidjan 2000-01-01      27.293
              Abidjan 2000-02-01      27.685
              Abidjan 2000-03-01      29.061
              Abidjan 2000-04-01      28.162
              Abidjan 2000-05-01      27.547
...                          ...         ...
China         Xian    2013-05-01      18.979
              Xian    2013-06-01      23.522
              Xian    2013-07-01      25.251
              Xian    2013-08-01      24.528
              Xian    2013-09-01         NaN

[16500 rows x 2 columns]
                         date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
```

Slicing is a technique for selecting consecutive elements from objects. 

Here are the dog breeds, this time as a list. To slice the list, you pass first and last positions separated by a colon into square brackets. Remember that Python positions start from zero, so 2 refers to the third element, Chow Chow. Also remember that the last position, 5, is not included in the slice, so we finish at Labrador, not Chihuahua. If you want the slice to start from the beginning of the list, you can omit the zero. Here, using colon-3 returns the first three elements. Slicing with colon on its own returns the whole list. 

<img width="1150" height="557" alt="image" src="https://github.com/user-attachments/assets/1517311f-f0d4-41fe-bac3-e1db1ff02f76" />

You can also slice DataFrames, but first, you need to sort the index. Here, the dogs dataset has been given a multi-level index of breed and color; then, the index is sorted with sort_index. 

<img width="1153" height="525" alt="image" src="https://github.com/user-attachments/assets/97c731e6-155f-45f4-8930-61fbc33d41bb" />

To slice rows at the outer level of an index, you call loc, passing the first and last values separated by a colon. The full dataset is shown on the right for comparison. There are two differences compared to slicing lists. Rather than specifying row numbers, you specify index values. Secondly, notice that the final value is included. Here, Poodle is included in the results. 

<img width="1139" height="453" alt="image" src="https://github.com/user-attachments/assets/449d5c9f-cafb-4de4-bc96-8baa3a5dccf6" />

The same technique doesn't work on inner index levels. Here, trying to slice from Tan to Grey returns an empty DataFrame instead of the six dogs we wanted. It's important to understand the danger here. pandas doesn't throw an error to let you know that there is a problem, so be careful when coding. 

<img width="1157" height="449" alt="image" src="https://github.com/user-attachments/assets/35029149-06f5-40a9-851e-1e8074b3f780" />

The correct approach to slicing at inner index levels is to pass the first and last positions as tuples. Here, the first element to include is a tuple of Labrador and Brown. 

<img width="1138" height="438" alt="image" src="https://github.com/user-attachments/assets/7b145bd3-3b2a-444f-b1ea-86f981c72a82" />

Since DataFrames are two-dimensional objects, you can also slice columns. You do this by passing two arguments to loc. The simplest case involves subsetting columns but keeping all rows. To do this, pass a colon as the first argument to loc. As with slicing lists, a colon by itself means "keep everything." The second argument takes column names as the first and last positions to slice on. 

<img width="1141" height="453" alt="image" src="https://github.com/user-attachments/assets/16fb2550-36b9-4273-a00d-05f903daea33" />

You can slice on rows and columns at the same time: simply pass the appropriate slice to each argument. Here, you see the previous two slices being performed in the same line of code. 

<img width="1158" height="459" alt="image" src="https://github.com/user-attachments/assets/3f9ef414-9966-4e0f-b2d9-b307d681f178" />

An important use case of slicing is to subset DataFrames by a range of dates. To demonstrate this, let's set the date_of_birth column as the index and sort by this index. 

<img width="1136" height="508" alt="image" src="https://github.com/user-attachments/assets/6384288b-a4ab-4e05-b27a-23cc29ceda02" />

You slice dates with the same syntax as other types. The first and last dates are passed as strings. 

<img width="1138" height="407" alt="image" src="https://github.com/user-attachments/assets/cd13f3fd-2d77-4465-ac50-e9a8588bf750" />

One helpful feature is that you can slice by partial dates. Here, the first and last positions are only specified as 2014 and 2016, with no month or day parts. pandas interprets this as slicing from the start of 2014 to the end of 2016; that is, all dates in 2014, 2015, and 2016. 

<img width="1148" height="407" alt="image" src="https://github.com/user-attachments/assets/0814432b-e928-4914-9063-562a9ba0800f" />

You can also slice DataFrames by row or column number using the iloc method. This uses a similar syntax to slicing lists, except that there are two arguments: one for rows and one for columns. Notice that, like list slicing but unlike loc, the final values aren't included in the slice. In this case, the fifth row and fourth column aren't included. 

<img width="1143" height="349" alt="image" src="https://github.com/user-attachments/assets/9f6d6372-ae52-4133-9247-1403d9ad84f9" />


## Exercise: Slicing index values

Slicing lets you select consecutive elements of an object using first:last syntax. DataFrames can be sliced by index values or by row/column number; we'll start with the first case. This involves slicing inside the .loc[] method.

Compared to slicing lists, there are a few things to remember.

    You can only slice an index if the index is sorted (using .sort_index()).
    To slice at the outer level, first and last can be strings.
    To slice at inner levels, first and last should be tuples.
    If you pass a single slice to .loc[], it will slice the rows.

pandas is loaded as pd. temperatures_ind has country and city in the index, and is available.


    Sort the index of temperatures_ind.
    Use slicing with .loc[] to get these subsets:
        from Pakistan to Philippines.
        from Lahore to Manila. (This will return nonsense.)
        from Pakistan, Lahore to Philippines, Manila.

## Solution

```python
# Sort the index of temperatures_ind
temperatures_srt = temperatures_ind.sort_index()

# Subset rows from Pakistan to Philippines
print(temperatures_srt.loc["Pakistan":"Philippines"])

# Try to subset rows from Lahore to Manila
print(temperatures_srt.loc["Lahore":"Manila"])

# Subset rows from Pakistan, Lahore to Philippines, Manila
print(temperatures_srt.loc[("Pakistan", "Lahore"):("Philippines","Manila")])

##Results

                             date  avg_temp_c
country     city                             
Pakistan    Faisalabad 2000-01-01      12.792
            Faisalabad 2000-02-01      14.339
            Faisalabad 2000-03-01      20.309
            Faisalabad 2000-04-01      29.072
            Faisalabad 2000-05-01      34.845
...                           ...         ...
Philippines Manila     2013-05-01      29.552
            Manila     2013-06-01      28.572
            Manila     2013-07-01      27.266
            Manila     2013-08-01      26.754
            Manila     2013-09-01         NaN

[825 rows x 2 columns]
Empty DataFrame
Columns: [date, avg_temp_c]
Index: []
                         date  avg_temp_c
country     city                         
Pakistan    Lahore 2000-01-01      12.792
            Lahore 2000-02-01      14.339
            Lahore 2000-03-01      20.309
            Lahore 2000-04-01      29.072
            Lahore 2000-05-01      34.845
...                       ...         ...
Philippines Manila 2013-05-01      29.552
            Manila 2013-06-01      28.572
            Manila 2013-07-01      27.266
            Manila 2013-08-01      26.754
            Manila 2013-09-01         NaN

[495 rows x 2 columns]
```

## Exercise: Slicing in both directions

You've seen slicing DataFrames by rows and by columns, but since DataFrames are two-dimensional objects, it is often natural to slice both dimensions at once. That is, by passing two arguments to .loc[], you can subset by rows and columns in one go.

pandas is loaded as pd. temperatures_srt is indexed by country and city, has a sorted index, and is available.


    Use .loc[] slicing to subset rows from India, Hyderabad to Iraq, Baghdad.
    Use .loc[] slicing to subset columns from date to avg_temp_c.
    Slice in both directions at once from Hyderabad to Baghdad, and date to avg_temp_c.

## Solution

```python
# Subset rows from India, Hyderabad to Iraq, Baghdad
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad")])

# Subset columns from date to avg_temp_c
print(temperatures_srt.loc[:, "date":"avg_temp_c"])

# Subset in both directions at once
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad"), "date":"avg_temp_c"])

##Results

                        date  avg_temp_c
country city                            
India   Hyderabad 2000-01-01      23.779
        Hyderabad 2000-02-01      25.826
        Hyderabad 2000-03-01      28.821
        Hyderabad 2000-04-01      32.698
        Hyderabad 2000-05-01      32.438
...                      ...         ...
Iraq    Baghdad   2013-05-01      28.673
        Baghdad   2013-06-01      33.803
        Baghdad   2013-07-01      36.392
        Baghdad   2013-08-01      35.463
        Baghdad   2013-09-01         NaN

[2145 rows x 2 columns]
                         date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
                        date  avg_temp_c
country city                            
India   Hyderabad 2000-01-01      23.779
        Hyderabad 2000-02-01      25.826
        Hyderabad 2000-03-01      28.821
        Hyderabad 2000-04-01      32.698
        Hyderabad 2000-05-01      32.438
...                      ...         ...
Iraq    Baghdad   2013-05-01      28.673
        Baghdad   2013-06-01      33.803
        Baghdad   2013-07-01      36.392
        Baghdad   2013-08-01      35.463
        Baghdad   2013-09-01         NaN

[2145 rows x 2 columns]
```

## Exercise: Slicing time series

Slicing is particularly useful for time series since it's a common thing to want to filter for data within a date range. Add the date column to the index, then use .loc[] to perform the subsetting. The important thing to remember is to keep your dates in ISO 8601 format, that is, "yyyy-mm-dd" for year-month-day, "yyyy-mm" for year-month, and "yyyy" for year.

Recall from Chapter 1 that you can combine multiple Boolean conditions using logical operators, such as &. To do so in one line of code, you'll need to add parentheses () around each condition.

pandas is loaded as pd and temperatures, with no index, is available.


    Use Boolean conditions, not .isin() or .loc[], and the full date "yyyy-mm-dd", to subset temperatures for rows where the date column is in 2010 and 2011 and print the results.
    Set the index of temperatures to the date column and sort it.
    Use .loc[] to subset temperatures_ind for rows in 2010 and 2011.
    Use .loc[] to subset temperatures_ind for rows from August 2010 to February 2011.


## Solution

```python
# Use Boolean conditions to subset temperatures for rows in 2010 and 2011
temperatures_bool = temperatures[(temperatures["date"] >= "2010-01-01") & (temperatures["date"] <= "2011-12-31")]
print(temperatures_bool)

# Set date as the index and sort the index
temperatures_ind = temperatures.set_index("date").sort_index()

# Use .loc[] to subset temperatures_ind for rows in 2010 and 2011
print(temperatures_ind.loc["2010":"2011"])

# Use .loc[] to subset temperatures_ind for rows from Aug 2010 to Feb 2011
print(temperatures_ind.loc["2010-08":"2011-02"])

#Results
            date     city        country  avg_temp_c
120   2010-01-01  Abidjan  Côte D'Ivoire      28.270
121   2010-02-01  Abidjan  Côte D'Ivoire      29.262
122   2010-03-01  Abidjan  Côte D'Ivoire      29.596
123   2010-04-01  Abidjan  Côte D'Ivoire      29.068
124   2010-05-01  Abidjan  Côte D'Ivoire      28.258
...          ...      ...            ...         ...
16474 2011-08-01     Xian          China      23.069
16475 2011-09-01     Xian          China      16.775
16476 2011-10-01     Xian          China      12.587
16477 2011-11-01     Xian          China       7.543
16478 2011-12-01     Xian          China      -0.490

[2400 rows x 4 columns]
                  city    country  avg_temp_c
date                                         
2010-01-01  Faisalabad   Pakistan      11.810
2010-01-01   Melbourne  Australia      20.016
2010-01-01   Chongqing      China       7.921
2010-01-01   São Paulo     Brazil      23.738
2010-01-01   Guangzhou      China      14.136
...                ...        ...         ...
2011-12-01      Nagoya      Japan       6.476
2011-12-01   Hyderabad      India      23.613
2011-12-01        Cali   Colombia      21.559
2011-12-01        Lima       Peru      18.293
2011-12-01     Bangkok   Thailand      25.021

[2400 rows x 3 columns]
                city        country  avg_temp_c
date                                           
2010-08-01  Calcutta          India      30.226
2010-08-01      Pune          India      24.941
2010-08-01     Izmir         Turkey      28.352
2010-08-01   Tianjin          China      25.543
2010-08-01    Manila    Philippines      27.101
...              ...            ...         ...
2011-02-01     Kabul    Afghanistan       3.914
2011-02-01   Chicago  United States       0.276
2011-02-01    Aleppo          Syria       8.246
2011-02-01     Delhi          India      18.136
2011-02-01   Rangoon          Burma      26.631

[700 rows x 3 columns]
```

## Exercise: Subsetting by row/column number

The most common ways to subset rows are the ways we've previously discussed: using a Boolean condition or by index labels. However, it is also occasionally useful to pass row numbers.

This is done using .iloc[], and like .loc[], it can take two arguments to let you subset by rows and columns.

pandas is loaded as pd. temperatures (without an index) is available.

Use .iloc[] on temperatures to take subsets.

    Get the 23rd row, 2nd column (index positions 22 and 1).
    Get the first 5 rows (index positions 0 to 5).
    Get all rows, columns 3 and 4 (index positions 2 to 4).
    Get the first 5 rows, columns 3 and 4.

## Solution

```python
# Get 23rd row, 2nd column (index 22, 1)
print(temperatures.iloc[22, 1])

# Use slicing to get the first 5 rows
print(temperatures.iloc[:5])

# Use slicing to get columns 3 to 4
print(temperatures.iloc[:, 2:4])

# Use slicing in both directions at once
print(temperatures.iloc[:5, 2:4])

##Results
Abidjan
        date     city        country  avg_temp_c
0 2000-01-01  Abidjan  Côte D'Ivoire      27.293
1 2000-02-01  Abidjan  Côte D'Ivoire      27.685
2 2000-03-01  Abidjan  Côte D'Ivoire      29.061
3 2000-04-01  Abidjan  Côte D'Ivoire      28.162
4 2000-05-01  Abidjan  Côte D'Ivoire      27.547
             country  avg_temp_c
0      Côte D'Ivoire      27.293
1      Côte D'Ivoire      27.685
2      Côte D'Ivoire      29.061
3      Côte D'Ivoire      28.162
4      Côte D'Ivoire      27.547
...              ...         ...
16495          China      18.979
16496          China      23.522
16497          China      25.251
16498          China      24.528
16499          China         NaN

[16500 rows x 2 columns]
         country  avg_temp_c
0  Côte D'Ivoire      27.293
1  Côte D'Ivoire      27.685
2  Côte D'Ivoire      29.061
3  Côte D'Ivoire      28.162
4  Côte D'Ivoire      27.547
```

You saw how to create pivot tables with pandas in chapter two. In this lesson, you'll perform subsetting and calculations on pivot tables.

Here's a larger version of the dog dataset. The extra dogs mean we have something to compute on. 

<img width="1138" height="550" alt="image" src="https://github.com/user-attachments/assets/c46e7f1f-e689-442e-b4f4-a99c83f7fccc" />

Recall that you create a pivot table by calling dot-pivot_table. The first argument is the column name containing values to aggregate. The index argument lists the columns to group by and display in rows, and the columns argument lists the columns to group by and display in columns. We'll use the default aggregation function, which is mean. 

<img width="1137" height="540" alt="image" src="https://github.com/user-attachments/assets/39ef8f70-dedc-48eb-9387-ccd642bb7d1d" />

Pivot tables are just DataFrames with sorted indexes. That means that all the fun stuff you've learned so far this chapter can be used on them. In particular, the loc and slicing combination is ideal for subsetting pivot tables, like so. 

<img width="1157" height="417" alt="image" src="https://github.com/user-attachments/assets/5a11affd-0bd7-4d08-a36b-2290a7f1b2c0" />

The methods for calculating summary statistics on a DataFrame, such as mean, have an axis argument. The default value is "index," which means "calculate the statistic across rows." Here, the mean is calculated for each color. That is, "across the breeds." The behavior is the same as if you hadn't specified the axis argument. 

<img width="1135" height="438" alt="image" src="https://github.com/user-attachments/assets/7ad25948-4690-43dc-a16d-2323ace1c698" />

To calculate a summary statistic for each row, that is, "across the columns," you set axis to "columns." Here, the mean height is calculated for each breed. That is, "across the colors." For most DataFrames, setting the axis argument doesn't make any sense, since you'll have different data types in each column. Pivot tables are a special case since every column contains the same data type. 

<img width="1138" height="543" alt="image" src="https://github.com/user-attachments/assets/e22e5e69-0805-41c0-acf4-eb5d5041a24c" />


## Exercise: Pivot temperature by city and year

It's interesting to see how temperatures for each city change over time—looking at every month results in a big table, which can be tricky to reason about. Instead, let's look at how temperatures change by year.

You can access the components of a date (year, month and day) using code of the form `dataframe["column"].dt.component`. For example, the month component is `dataframe["column"].dt.month`, and the year component is `dataframe["column"].dt.year`.

Once you have the year column, you can create a pivot table with the data aggregated by city and year, which you'll explore in the coming exercises.

pandas is loaded as pd. temperatures is available.

    
    Add a year column to temperatures, from the year component of the date column.
    Make a pivot table of the avg_temp_c column, with country and city as rows, and year as columns. Assign to temp_by_country_city_vs_year, and look at the result.

## Solution

```python
# Add a year column to temperatures
temperatures["year"] = temperatures["date"].dt.year

# Pivot avg_temp_c by country and city vs year
temp_by_country_city_vs_year = temperatures.pivot_table("avg_temp_c", index = ["country", "city"], columns = "year")

# See the result
print(temp_by_country_city_vs_year)

##Results
year                              2000    2001    2002    2003    2004  ...    2009    2010    2011    2012    2013
country       city                                                      ...                                        
Afghanistan   Kabul             15.823  15.848  15.715  15.133  16.128  ...  15.093  15.676  15.812  14.510  16.206
Angola        Luanda            24.410  24.427  24.791  24.867  24.216  ...  24.325  24.440  24.151  24.240  24.554
Australia     Melbourne         14.320  14.180  14.076  13.986  13.742  ...  14.647  14.232  14.191  14.269  14.742
              Sydney            17.567  17.854  17.734  17.592  17.870  ...  18.176  17.999  17.713  17.474  18.090
Bangladesh    Dhaka             25.905  25.931  26.095  25.927  26.136  ...  26.536  26.648  25.803  26.284  26.587
...                                ...     ...     ...     ...     ...  ...     ...     ...     ...     ...     ...
United States Chicago           11.090  11.703  11.532  10.482  10.943  ...  10.298  11.816  11.214  12.821  11.587
              Los Angeles       16.643  16.466  16.430  16.945  16.553  ...  16.677  15.887  15.875  17.090  18.121
              New York           9.969  10.931  11.252   9.836  10.389  ...  10.142  11.358  11.272  11.971  12.164
Vietnam       Ho Chi Minh City  27.589  27.832  28.065  27.828  27.687  ...  27.853  28.282  27.675  28.249  28.455
Zimbabwe      Harare            20.284  20.861  21.079  20.889  20.308  ...  20.524  21.166  20.782  20.523  19.756

[100 rows x 14 columns]
```

## Exercise: Subsetting pivot tables

A pivot table is just a DataFrame with sorted indexes, so the techniques you have learned already can be used to subset them. In particular, the .loc[] + slicing combination is often helpful.

pandas is loaded as pd. temp_by_country_city_vs_year is available.

    Use .loc[] on temp_by_country_city_vs_year to take subsets.
        From Egypt to India.
        From Egypt, Cairo to India, Delhi.
        From Egypt, Cairo to India, Delhi, and 2005 to 2010.

## Solution

```python
# Subset for Egypt to India
temp_by_country_city_vs_year.loc["Egypt":"India"]

# Subset for Egypt, Cairo to India, Delhi
temp_by_country_city_vs_year.loc[("Egypt", "Cairo"):("India", "Delhi")]

# Subset for Egypt, Cairo to India, Delhi, and 2005 to 2010
temp_by_country_city_vs_year.loc[("Egypt", "Cairo"):("India", "Delhi"), "2005":"2010"]

##Results

year                    2005    2006    2007    2008    2009    2010
country  city                                                       
Egypt    Cairo        22.006  22.050  22.361  22.644  22.625  23.718
         Gizeh        22.006  22.050  22.361  22.644  22.625  23.718
Ethiopia Addis Abeba  18.313  18.427  18.143  18.165  18.765  18.298
France   Paris        11.553  11.788  11.751  11.278  11.464  10.410
Germany  Berlin        9.919  10.545  10.883  10.658  10.062   8.607
India    Ahmadabad    26.828  27.283  27.511  27.049  28.096  28.018
         Bangalore    25.477  25.418  25.464  25.353  25.726  25.705
         Bombay       27.036  27.382  27.635  27.178  27.845  27.765
         Calcutta     26.729  26.986  26.585  26.522  27.153  27.289
         Delhi        25.716  26.366  26.146  25.675  26.554  26.520
```

## Exercise: Calculating on a pivot table

Pivot tables are filled with summary statistics, but they are only a first step to finding something insightful. Often you'll need to perform further calculations on them. A common thing to do is to find the rows or columns where the highest or lowest value occurs.

Recall from Chapter 1 that you can easily subset a Series or DataFrame to find rows of interest using a logical condition inside of square brackets. For example: series[series > value].

pandas is loaded as pd and the DataFrame temp_by_country_city_vs_year is available. The .head() for this DataFrame is shown below, with only a few of the year columns displayed:

<img width="726" height="294" alt="image" src="https://github.com/user-attachments/assets/9eb0a830-c163-4c71-a3a9-b67af299072a" />

    
    Calculate the mean temperature for each year, assigning to mean_temp_by_year.
    Filter mean_temp_by_year for the year that had the highest mean temperature.
    Calculate the mean temperature for each city (across columns), assigning to mean_temp_by_city.
    Filter mean_temp_by_city for the city that had the lowest mean temperature.

## Solution

```python
# Get the worldwide mean temp by year
mean_temp_by_year = temp_by_country_city_vs_year.mean()

# Filter for the year that had the highest mean temp
print(mean_temp_by_year[mean_temp_by_year == mean_temp_by_year.max()])

# Get the mean temp by city
mean_temp_by_city = temp_by_country_city_vs_year.mean(axis="columns")

# Filter for the city that had the lowest mean temp
print(mean_temp_by_city[mean_temp_by_city == mean_temp_by_city.min()])

##Results
year
2013    20.312
dtype: float64
country  city  
China    Harbin    4.877
dtype: float64
```
# Creating and Visualizing DataFrames

Plots are a powerful way to share the insights you've gained from your data. In this lesson, we'll use a bigger dataset of dogs, called dog_pack, to make visualization easier. 

Remember when we talked about matplotlib at the beginning of the course? We'll need to import matplotlib-dot-pyplot as plt in order to display our visualizations. Just like pd is the standard alias for pandas, plt is the standard alias for matplotlib-dot-pyplot. Let's create a histogram, which shows the distribution of a numeric variable. We can create a histogram of the height variable by selecting the column and calling dot-hist. In order to show the plot, we need to call plt-dot-show. The x-axis represents the heights of the dogs, and the y-axis represents the number of dogs in each height range. By grouping observations into ranges, the histogram allows us to see that there are a lot of dogs around 50 to 60 centimeters tall. 

<img width="1135" height="435" alt="image" src="https://github.com/user-attachments/assets/f161df16-0a22-4fa2-ba5a-f041f472431b" />

We can adjust the number of bars, or bins, using the "bins" argument. Increasing or decreasing this can give us a better idea of what the distribution looks like. 

<img width="1148" height="540" alt="image" src="https://github.com/user-attachments/assets/59deb73f-268f-4760-a5d6-d39b997f7946" />

Bar plots can reveal relationships between a categorical variable and a numeric variable, like breed and weight. To compute the average weight of each breed, we group by breed, select the weight column, and take the mean, giving us the average weight of each breed. 

<img width="1134" height="537" alt="image" src="https://github.com/user-attachments/assets/fbc2c249-7649-4d08-91e1-709f6191624f" />

Now we can create a bar plot from the mean weights using the plot method, setting "kind" equal to "bar." Finally, we call plt-dot-show. To add a title to our plot, we can use the title argument of the plot method. It looks like Saint Bernards are the heaviest breed on average! Woof! 

<img width="1165" height="549" alt="image" src="https://github.com/user-attachments/assets/54a66083-4bb5-4c6e-abbd-9527f0da86a2" />

Line plots are great for visualizing changes in numeric variables over time. Lucky for us, a Labrador named Sully has been weighed by his owner every month - let's see how his weight has changed over the year. We can use the plot method again, but this time, we pass in three arguments: date as x, weight as y, and "kind" equals "line." Sully's weight has fluctuated quite a bit over the year! 

<img width="1134" height="551" alt="image" src="https://github.com/user-attachments/assets/52bc74ae-5300-40e5-8e00-d896e5b5fbb9" />

We may want to rotate the x-axis labels to make the text easier to read. This can be done by passing an angle in degrees with the "rot" argument. Here, we rotate the labels by 45 degrees. 

<img width="1151" height="552" alt="image" src="https://github.com/user-attachments/assets/9af37a1f-1e90-4cf8-ae2e-a7d0591a92b6" />

Scatter plots are great for visualizing relationships between two numeric variables. To plot each dog's height versus their weight, we call the plot method with x equal to height_cm, y equal to weight_kg, and "kind" equal to "scatter." From our plot, it looks like taller dogs tend to weigh more. 

<img width="1130" height="546" alt="image" src="https://github.com/user-attachments/assets/87d19199-528e-4fcc-944f-140c4287a00c" />

Plots can also be layered on top of one another. For example, we can create a histogram of female dogs' heights, and put a histogram of male dogs' heights on top, then call show. However, we can't tell which color represents which sex. 

<img width="1156" height="543" alt="image" src="https://github.com/user-attachments/assets/c58cfe43-2f9b-45e1-9239-a6136b663e46" />

We can use plt-dot-legend, passing in a list of labels, and then call show. Now we know which color is which, but we can't see what's going on behind the orange histogram. 

<img width="1159" height="545" alt="image" src="https://github.com/user-attachments/assets/6a8b1d3b-9a32-4eb3-b54e-83bc73189b3a" />

Let's fix this problem by making the histograms translucent. We can use hist's alpha argument, which takes a number. 0 means completely transparent that is, invisible, and 1 means completely opaque. 

<img width="1145" height="545" alt="image" src="https://github.com/user-attachments/assets/3b8edbcf-e330-43e1-b156-0a021ab07f58" />


In this chapter, you'll be working with a dataset that contains weekly US avocado sales data, broken down by avocado size, and whether or not the avocados were organic. 

<img width="1146" height="530" alt="image" src="https://github.com/user-attachments/assets/7898d77f-6bb1-4234-af94-957134a6af95" />

## Exercise: Which avocado size is most popular?

Avocados are increasingly popular and delicious in guacamole and on toast. The Hass Avocado Board keeps track of avocado supply and demand across the USA, including the sales of three different sizes of avocado. In this exercise, you'll use a bar plot to figure out which size is the most popular.

Bar plots are great for revealing relationships between categorical (size) and numeric (number sold) variables, but you'll often have to manipulate your data first in order to get the numbers you need for plotting.

pandas has been imported as pd, and avocados is available.

    
    Print the head of the avocados dataset. What columns are available?
    For each avocado size group, calculate the total number sold, storing as nb_sold_by_size.
    Create a bar plot of the number of avocados sold by size.
    Show the plot.

## Solution
```python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Look at the first few rows of data
print(avocados.head())

# Get the total number of avocados sold of each size
nb_sold_by_size = avocados.groupby("size")["nb_sold"].sum()

# Create a bar plot of the number of avocados sold by size
nb_sold_by_size.plot(kind="bar")

# Show the plot
plt.show()

##Results
         date          type  year  avg_price   size    nb_sold
0  2015-12-27  conventional  2015       0.95  small  9.627e+06
1  2015-12-20  conventional  2015       0.98  small  8.710e+06
2  2015-12-13  conventional  2015       0.93  small  9.855e+06
3  2015-12-06  conventional  2015       0.89  small  9.405e+06
4  2015-11-29  conventional  2015       0.99  small  8.095e+06
```

<img width="1300" height="819" alt="image" src="https://github.com/user-attachments/assets/e8a603fc-f861-47ba-a901-56eded918d7a" />

## Exercise: Changes in sales over time

Line plots are designed to visualize the relationship between two numeric variables, where each data values is connected to the next one. They are especially useful for visualizing the change in a number over time since each time point is naturally connected to the next time point. In this exercise, you'll visualize the change in avocado sales over three years.

pandas has been imported as pd, and avocados is available.

    
    Get the total number of avocados sold on each date. The DataFrame has two rows for each date—one for organic, and one for conventional. Save this as nb_sold_by_date.
    Create a line plot of the number of avocados sold.
    Show the plot.

## Solution

```python
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Get the total number of avocados sold on each date
nb_sold_by_date = avocados.groupby("date")["nb_sold"].sum()

# Create a line plot of the number of avocados sold by date
nb_sold_by_date.plot(kind="line")

# Show the plot
plt.show()
```

<img width="1223" height="549" alt="image" src="https://github.com/user-attachments/assets/03044bec-1f0b-4ff4-aa95-0111e7e6520b" />

## Exercise: Avocado supply and demand

Scatter plots are ideal for visualizing relationships between numerical variables. In this exercise, you'll compare the number of avocados sold to average price and see if they're at all related. If they're related, you may be able to use one number to predict the other.

matplotlib.pyplot has been imported as plt, pandas has been imported as pd, and avocados is available.

## Solution

```python
# Scatter plot of avg_price vs. nb_sold with title
avocados.plot(x="nb_sold", y="avg_price", kind="scatter", title="Number of avocados sold vs. average price")

# Show the plot
plt.show()
```
<img width="1160" height="507" alt="image" src="https://github.com/user-attachments/assets/acc8d0f6-eab8-42ad-9533-d1a2452bbbe5" />

## Exercise: Price of conventional vs. organic avocados

Creating multiple plots for different subsets of data allows you to compare groups. In this exercise, you'll create multiple histograms to compare the prices of conventional and organic avocados.

matplotlib.pyplot has been imported as plt and pandas has been imported as pd.


    Subset avocados for the "conventional" type and create a histogram of the avg_price column.
    Create a histogram of avg_price for "organic" type avocados.
    Add a legend to your plot, with the names "conventional" and "organic".
    Show your plot.
    Modify your code to adjust the transparency of both histograms to 0.5 to see how much overlap there is between the two distributions.
    Modify your code to use 20 bins in both histograms.

## Solution

```python
# Histogram of conventional avg_price 
avocados[avocados["type"] == "conventional"]["avg_price"].hist()

# Histogram of organic avg_price
avocados[avocados["type"] == "organic"]["avg_price"].hist()

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
<img width="1209" height="453" alt="image" src="https://github.com/user-attachments/assets/bae15ccf-0ac8-4eb4-8bda-094dc3bae453" />

```python
# Modify histogram transparency to 0.5 
avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5)

# Modify histogram transparency to 0.5
avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
<img width="1502" height="510" alt="image" src="https://github.com/user-attachments/assets/4c1ca790-adc5-4f0b-89fd-abe995cb236d" />

```python
# Modify bins to 20
avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5, bins=20)

# Modify bins to 20
avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5, bins=20)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
<img width="1512" height="521" alt="image" src="https://github.com/user-attachments/assets/a451d180-f864-4560-874b-52919d0f3691" />



