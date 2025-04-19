# Intermediate Python

Learning Python is crucial for any aspiring data science practitioner. Learn to visualize real data with Matplotlib’s functions and get acquainted with data structures such as the dictionary and pandas DataFrame. This four-hour intermediate course will help you to build on your existing Python skills and explore new Python applications and functions that expand your repertoire and help you work more efficiently.

You'll discover how dictionaries offer an alternative to Python lists, and why the pandas dataframe is the most popular way of working with tabular data. In the second chapter of this course, you’ll find out how you can create and manipulate datasets, and how to access them using these structures. Hands-on practice throughout the course will build your confidence in each area.

As you progress, you’ll look at logic, control flow, filtering and loops. These functions work to control decision-making in Python programs and help you to perform more operations with your data, including repeated statements. You’ll finish the course by applying all of your new skills by using hacker statistics to calculate your chances of winning a bet.

Once you’ve completed all of the chapters, you’ll be ready to apply your new skills in your job, new career, or personal project, and be prepared to move onto more advanced Python learning.

----------

✅ [Matplotlib](https://github.com/janaom/datacamp-python-data-learning/blob/main/intermediate-python/README.md#matplotlib)

✅ [Dictionaries & Pandas](https://github.com/janaom/datacamp-python-data-learning/blob/main/intermediate-python/README.md#dictionaries--pandas)

✅ [Logic, Control Flow and Filtering](https://github.com/janaom/datacamp-python-data-learning/blob/main/intermediate-python/README.md#logic-control-flow-and-filtering)

✅ [Loops](https://github.com/janaom/datacamp-python-data-learning/blob/main/intermediate-python/README.md#loops)

✅ Case Study: Hacker Statistics

---------------

# Matplotlib

There are many visualization packages in python, but the mother of them all, is matplotlib. You will need its subpackage pyplot. By convention, this subpackage is imported as plt, like this. For our first example, let's try to gain some insights in the evolution of the world population. I have a list with years here, year, and a list with corresponding populations, expressed in billions, pop. In the year 1970, for example, 3.7 billion people lived on planet Earth. To plot this data as a line chart, we call plt-dot-plot and use our two lists as arguments. The first argument corresponds to the horizontal axis, and the second one to the vertical axis. You might think that a plot will pop up right now, but Python's pretty lazy. It will wait for the show function to actually display the plot. This is because you might want to add some extra ingredients to your plot before actually displaying it, such as titles and label customizations. I'll talk about that some more later on. Just remember this: the plot function tells Python what to plot and how to plot it. show actually displays the plot.

![image](https://github.com/user-attachments/assets/d7a43db3-03a9-4a6f-940b-3d89199eb08a)

When we look at our plot, we see that the years are indeed shown on the horizontal axis, and the populations on the vertical axis.

There are four data points, and Python draws a line between them. In 1950, the world population was around 2 point 5 billion. In 2010, it was around 7 billion. So the world population has almost tripled in sixty years. What if the population keeps on growing like that? Will the world become over populated? You'll find out in the exercises.

![image](https://github.com/user-attachments/assets/af295513-651c-4fe8-a250-db5b258348c7)

Let me first introduce you to another type of plot: the scatter plot. To create it, we can start from the code from before. This time, though, you change the plot function to scatter.

The resulting scatter plot simply plots all the individual data points; Python doesn't connect the dots with a line. For many applications, the scatter plot is often a better choice than the line plot, so remember this scatter function well. You could also say that this is a more -honest- way of plotting your data, because you can clearly see that the plot is based on just four data points.

![image](https://github.com/user-attachments/assets/0e06dd39-a659-48d7-9d69-66eb3f0d177d)

## Exercise: Line plot (1)

With matplotlib, you can create a bunch of different plots in Python. The most basic plot is the line plot. A general recipe is given here.

```python
import matplotlib.pyplot as plt
plt.plot(x,y)
plt.show()
```

In the video, you already saw how much the world population has grown over the past years. Will it continue to do so? The world bank has estimates of the world population for the years 1950 up to 2100. The years are loaded in your workspace as a list called year, and the corresponding populations as a list called pop.

    print() the last item from both the year and the pop list to see what the predicted population for the year 2100 is. Use two print() functions.
    
    Before you can start, you should import matplotlib.pyplot as plt. pyplot is a sub-package of matplotlib, hence the dot.
    
    Use plt.plot() to build a line plot. year should be mapped on the horizontal axis, pop on the vertical axis. Don't forget to finish off with the plt.show() function to       actually display the plot.

## Solution

```python
# Print the last item from year and pop
print(year[-1])
print(pop[-1])

# Import matplotlib.pyplot as plt
import matplotlib.pyplot as plt

# Make a line plot: year on the x-axis, pop on the y-axis
plt.plot(year, pop)

# Display the plot with plt.show()
plt.show()
```
Results

2100

10.85

![image](https://github.com/user-attachments/assets/d7c9edc3-fd85-4806-99c7-91a224601955)

## Exercise: Line plot (3)

Now that you've built your first line plot, let's start working on the data that professor Hans Rosling used to build his beautiful bubble chart. It was collected in 2007. Two lists are available for you:

- life_exp which contains the life expectancy for each country and
- gdp_cap, which contains the GDP per capita (i.e. per person) for each country expressed in US Dollars.
  
GDP stands for Gross Domestic Product. It basically represents the size of the economy of a country. Divide this by the population and you get the GDP per capita.

matplotlib.pyplot is already imported as plt, so you can get started straight away.

    Print the last item from both the list gdp_cap, and the list life_exp; it is information about Zimbabwe.
    Build a line chart, with gdp_cap on the x-axis, and life_exp on the y-axis. Does it make sense to plot this data on a line plot?
    Don't forget to finish off with a plt.show() command, to actually display the plot.

## Solution

```python
# Print the last item of gdp_cap and life_exp
print(gdp_cap[-1])
print(life_exp[-1])

# Make a line plot, gdp_cap on the x-axis, life_exp on the y-axis
plt.plot(gdp_cap, life_exp)

# Display the plot
plt.show()
```

Results

469.70929810000007

43.487

![image](https://github.com/user-attachments/assets/01aab404-2d0b-4f48-ab6d-05876c04982d)

## Exercise: Scatter Plot (1)

When you have a time scale along the horizontal axis, the line plot is your friend. But in many other cases, when you're trying to assess if there's a correlation between two variables, for example, the scatter plot is the better choice. Below is an example of how to build a scatter plot.

```python
import matplotlib.pyplot as plt
plt.scatter(x,y)
plt.show()
```

Let's continue with the gdp_cap versus life_exp plot, the GDP and life expectancy data for different countries in 2007. Maybe a scatter plot will be a better alternative?

Again, the matplotlib.pyplot package is available as plt.


    Change the line plot that's coded in the script to a scatter plot.
    A correlation will become clear when you display the GDP per capita on a logarithmic scale. Add the line plt.xscale('log').
    Finish off your script with plt.show() to display the plot.

## Solution

```python
# Change the line plot below to a scatter plot
plt.scatter(gdp_cap, life_exp)

# Put the x-axis on a logarithmic scale
plt.xscale('log')

# Show plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/5658d29c-2c7e-4a2f-bb1b-db795b600e2a)

## Exercise: Scatter Plot (2)

In the previous exercise, you saw that the higher GDP usually corresponds to a higher life expectancy. In other words, there is a positive correlation.

Do you think there's a relationship between population and life expectancy of a country? The list life_exp from the previous exercise is already available. In addition, now also pop is available, listing the corresponding populations for the countries in 2007. The populations are in millions of people.


    Start from scratch: import matplotlib.pyplot as plt.
    Build a scatter plot, where pop is mapped on the horizontal axis, and life_exp is mapped on the vertical axis.
    Finish the script with plt.show() to actually display the plot. Do you see a correlation?


## Solution

```python
# Import package
import matplotlib.pyplot as plt

# Build Scatter plot
plt.scatter(pop, life_exp)

# Show plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/6ed3d8ab-5965-477a-b04e-ba10ed4df7de)

The histogram is a type of visualization that's very useful to explore your data. It can help you to get an idea about the distribution of your variables. To see how it works, imagine 12 values between 0 and 6. 

![image](https://github.com/user-attachments/assets/9e9682f4-7d0b-40aa-b8c5-25399c5883cf)

## Exercise: Build a histogram (1)

life_exp, the list containing data on the life expectancy for different countries in 2007, is displayed.

To see how life expectancy in different countries is distributed, let's create a histogram of life_exp.

matplotlib.pyplot is already available as plt.


    Use plt.hist() to create a histogram of the values in life_exp. Do not specify the number of bins; Python will set the number of bins to 10 by default for you.
    Add plt.show() to actually display the histogram. Can you tell which bin contains the most observations?

## Solution

```python
# Create histogram of life_exp data
plt.hist(life_exp)

# Display histogram
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/96243f8d-4e43-466c-a581-58ba96ee587a)

## Exercise: Build a histogram (2): bins

In the previous exercise, you didn't specify the number of bins. By default, Python sets the number of bins to 10 in that case. The number of bins is pretty important. Too few bins will oversimplify reality and won't show you the details. Too many bins will overcomplicate reality and won't show the bigger picture.

To control the number of bins to divide your data in, you can set the bins argument.

That's exactly what you'll do in this exercise. You'll be making two plots here. The code in the script already includes plt.show() and plt.clf() calls; plt.show() displays a plot; plt.clf() cleans it up again so you can start afresh.

As before, life_exp is available and matplotlib.pyplot is imported as plt.


    Build a histogram of life_exp, with 5 bins. Can you tell which bin contains the most observations?
    Build another histogram of life_exp, this time with 20 bins. Is this better?

## Solution

```python
# Build histogram with 5 bins
plt.hist(life_exp, bins=5)

# Show and clean up plot
plt.show()
plt.clf()

# Build histogram with 20 bins
plt.hist(life_exp, bins=20)

# Show and clean up again
plt.show()
plt.clf()
```

Results

![image](https://github.com/user-attachments/assets/94df7e61-b04e-4f6b-a42b-8962146f5549)

![image](https://github.com/user-attachments/assets/e9bb39fe-843d-4a33-9dfd-8bd7a12d6373)

## Exercise: Build a histogram (3): compare

In the video, you saw population pyramids for the present day and for the future. Because we were using a histogram, it was very easy to make a comparison.

Let's do a similar comparison. life_exp contains life expectancy data for different countries in 2007. You also have access to a second list now, life_exp1950, containing similar data for 1950. Can you make a histogram for both datasets?

You'll again be making two plots. The plt.show() and plt.clf() commands to render everything nicely are already included. Also matplotlib.pyplot is imported for you, as plt.


    Build a histogram of life_exp with 15 bins.
    Build a histogram of life_exp1950, also with 15 bins. Is there a big difference with the histogram for the 2007 data?

## Solution

```python
# Histogram of life_exp, 15 bins
plt.hist(life_exp, bins=15)

# Show and clear plot
plt.show()
plt.clf()

# Histogram of life_exp1950, 15 bins
plt.hist(life_exp1950, bins=15)

# Show and clear plot again
plt.show()
plt.clf()
```

Results

![image](https://github.com/user-attachments/assets/3a1bb16c-907e-4a33-acec-e9f9bcb3eb85)

![image](https://github.com/user-attachments/assets/a76729fc-0a14-4604-b60b-a002f4f1549a)


## Customization

![image](https://github.com/user-attachments/assets/a68843fe-bf5d-431a-9614-35d1f500b6e3)

![image](https://github.com/user-attachments/assets/dac57fca-ac84-42b2-84c8-b6deade2967e)

## Exercise: Labels

It's time to customize your own plot. This is the fun part, you will see your plot come to life!

You're going to work on the scatter plot with world development data: GDP per capita on the x-axis (logarithmic scale), life expectancy on the y-axis. The code for this plot is available in the script.

As a first step, let's add axis labels and a title to the plot. You can do this with the xlabel(), ylabel() and title() functions, available in matplotlib.pyplot. This sub-package is already imported as plt.


    The strings xlab and ylab are already set for you. Use these variables to set the label of the x- and y-axis.
    The string title is also coded for you. Use it to add a title to the plot.
    After these customizations, finish the script with plt.show() to actually display the plot.

## Solution

```python
# Basic scatter plot, log scale
plt.scatter(gdp_cap, life_exp)
plt.xscale('log') 

# Strings
xlab = 'GDP per Capita [in USD]'
ylab = 'Life Expectancy [in years]'
title = 'World Development in 2007'

# Add axis labels
plt.xlabel(xlab)
plt.ylabel(ylab)

# Add title
plt.title(title)

# After customizing, display the plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/c1908f13-3a7c-401e-84f5-7ed9f25c829b)

## Exercise: Ticks

The customizations you've coded up to now are available in the script, in a more concise form.

In the video, Hugo has demonstrated how you could control the y-ticks by specifying two arguments:

```python
plt.yticks([0,1,2], ["one","two","three"])
```

In this example, the ticks corresponding to the numbers 0, 1 and 2 will be replaced by one, two and three, respectively.

Let's do a similar thing for the x-axis of your world development chart, with the xticks() function. The tick values 1000, 10000 and 100000 should be replaced by 1k, 10k and 100k. To this end, two lists have already been created for you: tick_val and tick_lab.


    Use tick_val and tick_lab as inputs to the xticks() function to make the the plot more readable.
    As usual, display the plot with plt.show() after you've added the customizations.

## Solution

```python
# Scatter plot
plt.scatter(gdp_cap, life_exp)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')

# Definition of tick_val and tick_lab
tick_val = [1000, 10000, 100000]
tick_lab = ['1k', '10k', '100k']

# Adapt the ticks on the x-axis
plt.xticks(tick_val, tick_lab)

# After customizing, display the plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/173c6943-cc96-43bd-a2bf-e192e7fca45b)

## Exercise: Sizes

Right now, the scatter plot is just a cloud of blue dots, indistinguishable from each other. Let's change this. Wouldn't it be nice if the size of the dots corresponds to the population?

To accomplish this, there is a list pop loaded in your workspace. It contains population numbers for each country expressed in millions. You can see that this list is added to the scatter method, as the argument s, for size.


    Run the script to see how the plot changes.
    Looks good, but increasing the size of the bubbles will make things stand out more.
        Import the numpy package as np.
        Use np.array() to create a numpy array from the list pop. Call this NumPy array np_pop.
        Double the values in np_pop setting the value of np_pop equal to np_pop * 2. Because np_pop is a NumPy array, each array element will be doubled.
        Change the s argument inside plt.scatter() to be np_pop instead of pop.

## Solution

```python
# Import numpy as np
import numpy as np

# Store pop as a numpy array: np_pop
np_pop=np.array(pop)

# Double np_pop
np_pop=np_pop * 2

# Update: set s argument to np_pop
plt.scatter(gdp_cap, life_exp, s = np_pop)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000, 10000, 100000],['1k', '10k', '100k'])

# Display the plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/8587db12-33c4-416a-b7d8-3fe011b52766)

## Exercise: Colors

The code you've written up to now is available in the script.

The next step is making the plot more colorful! To do this, a list col has been created for you. It's a list with a color for each corresponding country, depending on the continent the country is part of.

How did we make the list col you ask? The Gapminder data contains a list continent with the continent each country belongs to. A dictionary is constructed that maps continents onto colors:

```python
dict = {
    'Asia':'red',
    'Europe':'green',
    'Africa':'blue',
    'Americas':'yellow',
    'Oceania':'black'
}
```

Nothing to worry about now; you will learn about dictionaries in the next chapter.


    Add c = col to the arguments of the plt.scatter() function.
    Change the opacity of the bubbles by setting the alpha argument to 0.8 inside plt.scatter(). Alpha can be set from zero to one, where zero is totally transparent, and one is not at all transparent.

## Solution

```python
# Specify c and alpha inside plt.scatter()
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha = 0.8)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Show the plot
plt.show()
```

![image](https://github.com/user-attachments/assets/d08dde51-244f-46e1-8da8-ce5fae17557f)

## Exercise: Additional Customizations

If you have another look at the script, under # Additional Customizations, you'll see that there are two plt.text() functions now. They add the words "India" and "China" in the plot.

    Add plt.grid(True) after the plt.text() calls so that gridlines are drawn on the plot.

## Solution

```python
# Scatter plot
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha = 0.8)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Additional customizations
plt.text(1550, 71, 'India')
plt.text(5700, 80, 'China')

# Add grid() call
plt.grid(True)

# Show the plot
plt.show()
```

Results

![image](https://github.com/user-attachments/assets/95ba2d4a-e9cf-46eb-a82f-c35335180d39)

# Dictionaries & Pandas

So we built two lists, and used the index to connect corresponding elements in both lists. It worked, but it's a pretty terrible approach: it's not convenient and not intuitive. Wouldn't it be easier if we had a way to connect each country directly to its population, without using an index? This is where the dictionary comes into play.


![image](https://github.com/user-attachments/assets/4301de74-c5fd-461d-b05f-49d09fc10d01)

If you know want to find the population for Albania, you simply type world, and then the string Albania inside square brackets. In other words, you pass the key in square brackets, and you get the corresponding value. The key opens the door to the value: pretty poetic, isn't it? This approach is not only intuitive, it's also very efficient, because Python can make the lookup of these keys very fast, even for huge dictionaries.

![image](https://github.com/user-attachments/assets/3ab8d31a-b716-44a4-b39a-65e4074a5da8)

## Exercise: Motivation for dictionaries

To see why dictionaries are useful, have a look at the two lists defined in the script. countries contains the names of some European countries. capitals lists the corresponding names of their capital.

    Use the index() method on countries to find the index of 'germany'. Store this index as ind_ger.
    Use ind_ger to access the capital of Germany from the capitals list. Print it out.

## Solution

```python
# Definition of countries and capital
countries = ['spain', 'france', 'germany', 'norway']
capitals = ['madrid', 'paris', 'berlin', 'oslo']

# Get index of 'germany': ind_ger
ind_ger = countries.index('germany')

# Use ind_ger to print out capital of Germany
print(capitals[ind_ger])

#Results
berlin
```

## Exercise: Create dictionary

The countries and capitals lists are again available in the script. It's your job to convert this data to a dictionary where the country names are the keys and the capitals are the corresponding values. As a refresher, here is a recipe for creating a dictionary:

```python
my_dict = {
   "key1":"value1",
   "key2":"value2",
}
```

In this recipe, both the keys and the values are strings. This will also be the case for this exercise.

    With the strings in countries and capitals, create a dictionary called europe with 4 key:value pairs. Beware of capitalization! Make sure you use lowercase characters       everywhere.
    Print out europe to see if the result is what you expected.

## Solution

```python
# Definition of countries and capital
countries = ['spain', 'france', 'germany', 'norway']
capitals = ['madrid', 'paris', 'berlin', 'oslo']

# From string in countries and capitals, create dictionary europe
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo'}

# Print europe
print(europe)

#Results
{'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo'}
```

## Exercise: Access dictionary

If the keys of a dictionary are chosen wisely, accessing the values in a dictionary is easy and intuitive. For example, to get the capital for France from europe you can use:

```python
europe['france']
```

Here, 'france' is the key and 'paris' the value is returned.

    Check out which keys are in europe by calling the keys() method on europe. Print out the result.
    Print out the value that belongs to the key 'norway'.

## Solution

```python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Print out the keys in europe
print(europe.keys())

# Print out value that belongs to key 'norway'
print(europe['norway'])

#Results
dict_keys(['spain', 'france', 'germany', 'norway'])
oslo
```

Also, these unique keys in a dictionary should be so-called immutable objects. Basically, the content of immutable objects cannot be changed after they're created. Strings, booleans, integers and floats are immutable objects, but the list for example is mutable, because you can change its contents after it's created. That's why this dictionary, that has all immutable objects as keys, is perfectly valid. This one, however, that uses a list as a key, is not valid, so we get an error. 

![image](https://github.com/user-attachments/assets/72309452-0493-4fb4-96d2-4303352e24d3)

So now that you have an idea of how to build a valid dictionary and how to access it using square brackets, let's see how we can add more data to a dictionary that already exists.

To add this information, simply write the key sealand in square brackets and assign 27 expressed in millions to it with the equals sign. If you check out "world" again, indeed, sealand is in there. To check this with code, you can also write "sealand in world", which gives you True if the key sealand is in there.

![image](https://github.com/user-attachments/assets/b8ffad48-ed1a-4f92-81ef-c8c2cefeb22d)

With the same syntax, you can also change values, for example, to update the population of sealand to 28. Because each key in a dictionary is unique, Python knows that you're not trying to create a new pair, but want to update the pair that's already in there. You can see this from the printout here. Suppose now that your boss didn't see the humour of adding Sealand to the list, and asks you to remove it again. You can do this with del, again pointing to sealand inside square brackets. If you print world again, Sealand is no longer in there. Good riddance!

![image](https://github.com/user-attachments/assets/9fddb9f2-bde6-47cd-a8c4-8fde580bb11f)

![image](https://github.com/user-attachments/assets/8d19dc71-3223-405e-aaf9-68523ba3fedb)

## Exercise: Dictionary Manipulation (1)

If you know how to access a dictionary, you can also assign a new value to it. To add a new key-value pair to europe you can use something like this:

```python
europe['iceland'] = 'reykjavik'
```

    Add the key 'italy' with the value 'rome' to europe.
    To assert that 'italy' is now a key in europe, print out 'italy' in europe.
    Add another key:value pair to europe: 'poland' is the key, 'warsaw' is the corresponding value.
    Print out europe.

## Solution

```python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Add italy to europe
europe['italy'] = 'rome'

# Print out italy in europe
print('italy' in europe)

# Add poland to europe
europe['poland'] = 'warsaw'

# Print europe
print(europe)

#Results
    True
    {'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo', 'italy': 'rome', 'poland': 'warsaw'}
```

## Exercise: Dictionary Manipulation (2)

Somebody thought it would be funny to mess with your accurately generated dictionary. An adapted version of the europe dictionary is available in the script.

Can you clean up? Do not do this by adapting the definition of europe, but by adding Python commands to the script to update and remove key:value pairs.

    The capital of Germany is not 'bonn'; it's 'berlin'. Update its value.
    Australia is not in Europe, Austria is! Remove the key 'australia' from europe.
    Print out europe to see if your cleaning work paid off.

## Solution

```python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'bonn',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw',
          'australia':'vienna' }

# Update capital of germany
europe['germany'] = 'berlin'

# Remove australia
del(europe['australia'])

# Print europe
print(europe)

#Results
{'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo', 'italy': 'rome', 'poland': 'warsaw'}
```

## Exercise: Dictionariception

Remember lists? They could contain anything, even other lists. Well, for dictionaries the same holds. Dictionaries can contain key:value pairs where the values are again dictionaries.

As an example, have a look at the script where another version of europe - the dictionary you've been working with all along - is coded. The keys are still the country names, but the values are dictionaries that contain more information than just the capital.

It's perfectly possible to chain square brackets to select elements. To fetch the population for Spain from europe, for example, you need:

```python
europe['spain']['population']
```

    Use chained square brackets to select and print out the capital of France.
    Create a dictionary, named data, with the keys 'capital' and 'population'. Set them to 'rome' and 59.83, respectively.
    Add a new key-value pair to europe; the key is 'italy' and the value is data, the dictionary you just built.

## Solution

```python
# Dictionary of dictionaries
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }


# Print out the capital of France
print(europe['france']['capital'])

# Create sub-dictionary data
data = { 'capital':'rome', 'population':59.83 }

# Add data to europe under key 'italy'
europe['italy'] = data

# Print europe
print(europe)

#Results
paris
{'spain': {'capital': 'madrid', 'population': 46.77}, 'france': {'capital': 'paris', 'population': 66.03}, 'germany': {'capital': 'berlin', 'population': 80.62}, 'norway': {'capital': 'oslo', 'population': 5.084}, 'italy': {'capital': 'rome', 'population': 59.83}}
```

Pandas is a high level data manipulation tool developed by Wes McKinney, built on the NumPy package. Compared to NumPy, it's more high level, making it very interesting for data scientists all over the world. In pandas, we store the tabular data like the brics table here in an object called a DataFrame. 

First of all, you can build it manually, starting from a dictionary. Using the distinctive curly brackets, we create key value pairs. The keys are the column labels, and the values are the corresponding columns, in list form. After importing the pandas package as pd, you can create a DataFrame from the dictionary using pd (dot) DataFrame.

![image](https://github.com/user-attachments/assets/cb03310f-76ac-4aef-af84-9668b578900d)

If you check out brics now, we're almost there. Pandas assigned some automatic row labels, 0 up to 4. To specify them manually, you can set the index attribute of brics to a list with the correct labels. The resulting brics DataFrame is the same one as you saw before. Using a dictionary approach is fine, but what if you're working with tons of data, which is typically the case as a data scientist? Well, you won't build the DataFrame manually. Instead, you import data from an external file that contains all this data.

![image](https://github.com/user-attachments/assets/b10d62e1-1fb5-4f54-869e-8b433be75792)

Let's try to import this data into Python using Pandas read_csv function. You pass the path to the csv file as an argument. If you now print brics, there's still something wrong. The row labels are seen as a column in their own right. 

![image](https://github.com/user-attachments/assets/b950a79e-beb1-4c43-bb97-c6642bb9a3cd)

To solve this, we'll have to tell the read_csv function that the first column contains the row indexes. You do this by setting the index_col argument, like this.

![image](https://github.com/user-attachments/assets/975834d7-7168-4290-ad4c-e94f4d5f5d05)


## Exercise: Dictionary to DataFrame (1)

Pandas is an open source library, providing high-performance, easy-to-use data structures and data analysis tools for Python. Sounds promising!

The DataFrame is one of Pandas' most important data structures. It's basically a way to store tabular data where you can label the rows and the columns. One way to build a DataFrame is from a dictionary.

In the exercises that follow you will be working with vehicle data from different countries. Each observation corresponds to a country and the columns give information about the number of vehicles per capita, whether people drive left or right, and so on.

Three lists are defined in the script:

- names, containing the country names for which data is available.
- dr, a list with booleans that tells whether people drive left or right in the corresponding country.
- cpc, the number of motor vehicles per 1000 people in the corresponding country.
- Each dictionary key is a column label and each value is a list which contains the column elements.

        Import pandas as pd.
        Use the pre-defined lists to create a dictionary called my_dict. There should be three key value pairs:
        key 'country' and value names.
        key 'drives_right' and value dr.
        key 'cars_per_cap' and value cpc.
        Use pd.DataFrame() to turn your dict into a DataFrame called cars.
        Print out cars and see how beautiful it is.

## Solution

```python
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd
import pandas as pd

# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = { 'country':names, 'drives_right':dr, 'cars_per_cap':cpc }

# Build a DataFrame cars from my_dict: cars
cars = pd.DataFrame(my_dict)

# Print cars
print(cars)

#Results

         country  drives_right  cars_per_cap
0  United States          True           809
1      Australia         False           731
2          Japan         False           588
3          India         False            18
4         Russia          True           200
5        Morocco          True            70
6          Egypt          True            45
```

## Exercise: Dictionary to DataFrame (2)

The Python code that solves the previous exercise is included in the script. Have you noticed that the row labels (i.e. the labels for the different observations) were automatically set to integers from 0 up to 6?

To solve this a list row_labels has been created. You can use it to specify the row labels of the cars DataFrame. You do this by setting the index attribute of cars, that you can access as cars.index.

    Hit Run Code to see that, indeed, the row labels are not correctly set.
    Specify the row labels by setting cars.index equal to row_labels.
    Print out cars again and check if the row labels are correct this time.

## Solution

```python
import pandas as pd

# Build cars DataFrame
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]
cars_dict = { 'country':names, 'drives_right':dr, 'cars_per_cap':cpc }
cars = pd.DataFrame(cars_dict)
print(cars)

# Definition of row_labels
cars.index = ['US', 'AUS', 'JPN', 'IN', 'RU', 'MOR', 'EG']

# Specify row labels of cars
print(cars)

#Results

         country  drives_right  cars_per_cap
0  United States          True           809
1      Australia         False           731
2          Japan         False           588
3          India         False            18
4         Russia          True           200
5        Morocco          True            70
6          Egypt          True            45
           country  drives_right  cars_per_cap
US   United States          True           809
AUS      Australia         False           731
JPN          Japan         False           588
IN           India         False            18
RU          Russia          True           200
MOR        Morocco          True            70
EG           Egypt          True            45
```

## Exercise: CSV to DataFrame (1)

Putting data in a dictionary and then building a DataFrame works, but it's not very efficient. What if you're dealing with millions of observations? In those cases, the data is typically available as files with a regular structure. One of those file types is the CSV file, which is short for "comma-separated values".

To import CSV data into Python as a Pandas DataFrame you can use read_csv().

Let's explore this function with the same cars data from the previous exercises. This time, however, the data is available in a CSV file, named cars.csv. It is available in your current working directory, so the path to the file is simply 'cars.csv'.


    To import CSV files you still need the pandas package: import it as pd.
    Use pd.read_csv() to import cars.csv data as a DataFrame. Store this DataFrame as cars.
    Print out cars. Does everything look OK?

## Solution

```python
# Import pandas as pd
import pandas as pd

# Import the cars.csv data: cars
cars=pd.read_csv("cars.csv")

# Print out cars
print(cars)

#Results

      Unnamed: 0  cars_per_cap        country  drives_right
    0         US           809  United States          True
    1        AUS           731      Australia         False
    2        JPN           588          Japan         False
    3         IN            18          India         False
    4         RU           200         Russia          True
    5        MOR            70        Morocco          True
    6         EG            45          Egypt          True
```

## Exercise: CSV to DataFrame (2)

Your read_csv() call to import the CSV data didn't generate an error, but the output is not entirely what we wanted. The row labels were imported as another column without a name.

Remember index_col, an argument of read_csv(), that you can use to specify which column in the CSV file should be used as a row label? Well, that's exactly what you need here!

Python code that solves the previous exercise is already included; can you make the appropriate changes to fix the data import?


    Run the code with Run Code and assert that the first column should actually be used as row labels.
    Specify the index_col argument inside pd.read_csv(): set it to 0, so that the first column is used as row labels.
    Has the printout of cars improved now?

## Solution

```python
# Import pandas as pd
import pandas as pd

# Fix import by including index_col
cars = pd.read_csv('cars.csv', index_col=0)

# Print out cars
print(cars)

#Results

     cars_per_cap        country  drives_right
US            809  United States          True
AUS           731      Australia         False
JPN           588          Japan         False
IN             18          India         False
RU            200         Russia          True
MOR            70        Morocco          True
EG             45          Egypt          True
```

There are numerous ways in which you can index and select data from DataFrames, so we'll take this step by step. First, I'm going to talk about how to use square brackets; next, I'm going to tell you about advanced data access methods, loc and iloc, that make Pandas extra powerful. 

![image](https://github.com/user-attachments/assets/5f1212e6-b82c-41b3-9d10-835287e3e918)

![image](https://github.com/user-attachments/assets/2108e03d-bfa8-403d-be66-c5fb957dd8e0)

You can also use the same square brackets to select rows from a DataFrame. The way to do it is by specifying a slice. To get the second, third and fourth rows of brics, we use the slice 1 colon 4. Remember that the end of the slice is exclusive and that the index starts at zero. 

![image](https://github.com/user-attachments/assets/c5f8291f-c1f1-4b84-9b48-9886fb7db6de)

These square brackets work, but it only offers limited functionality. Ideally, we'd want something similar to 2D NumPy arrays. There, you also used square brackets, the index or slice before the comma referred to the rows, the index or slice after the comma referred to the columns. If we want to do a similar thing with Pandas, we have to extend our toolbox with the loc and iloc functions. loc is a technique to select parts of your data based on labels, iloc is position based. Let's start with loc first. 

![image](https://github.com/user-attachments/assets/feb0fb41-785f-4d6f-a58d-eed389c56e81)

Let's have another look at the brics DataFrame, and try to get the row for Russia. This is how it's done. You put the label of the row of interest in square brackets after loc. Again, we get a Pandas Series, containing all the row's information, rather inconveniently shown on different lines. 

![image](https://github.com/user-attachments/assets/7d766585-d913-4543-8436-6e1ac69e1d70)

![image](https://github.com/user-attachments/assets/779dc0f0-5870-477a-b689-755de1bfc5a8)

![image](https://github.com/user-attachments/assets/c816e7b5-9afc-4c32-a89d-4c5ceb258d2b)


Of course, you can also use loc to select all rows but only a specific number of columns. Simply replace the first list that specifies the row labels with a colon, a slice going from beginning to end. This time, the intersection spans all rows, but only two columns. 

![image](https://github.com/user-attachments/assets/5d9ae19e-96d2-4184-8623-614ff85fbc5d)

![image](https://github.com/user-attachments/assets/44c661e5-6858-437a-ab0d-c43ff08870a9)

![image](https://github.com/user-attachments/assets/19b8002e-a1ab-42c9-a479-8eb3e1dbafd0)

![image](https://github.com/user-attachments/assets/da0cc610-aad1-4097-b6db-974d53e6c0b2)

![image](https://github.com/user-attachments/assets/1cef5a60-edee-47b7-b87d-067bd3b15c97)

![image](https://github.com/user-attachments/assets/02f71f48-5fc2-4f97-8f09-8b7421f3bd60)

## Exercise: Square Brackets (1)

In the video, you saw that you can index and select Pandas DataFrames in many different ways. The simplest, but not the most powerful way, is to use square brackets.

In the sample code, the same cars data is imported from a CSV files as a Pandas DataFrame. To select only the cars_per_cap column from cars, you can use:

```python
cars['cars_per_cap']
cars[['cars_per_cap']]
```

The single bracket version gives a Pandas Series, the double bracket version gives a Pandas DataFrame.


    Use single square brackets to print out the country column of cars as a Pandas Series.
    Use double square brackets to print out the country column of cars as a Pandas DataFrame.
    Use double square brackets to print out a DataFrame with both the country and drives_right columns of cars, in this order.


## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out country column as Pandas Series
print(cars['country'])

# Print out country column as Pandas DataFrame
print(cars[['country']])

# Print out DataFrame with country and drives_right columns
print(cars[['country','drives_right']])

#Results

    US     United States
    AUS        Australia
    JPN            Japan
    IN             India
    RU            Russia
    MOR          Morocco
    EG             Egypt
    Name: country, dtype: object
               country
    US   United States
    AUS      Australia
    JPN          Japan
    IN           India
    RU          Russia
    MOR        Morocco
    EG           Egypt
               country  drives_right
    US   United States          True
    AUS      Australia         False
    JPN          Japan         False
    IN           India         False
    RU          Russia          True
    MOR        Morocco          True
    EG           Egypt          True
```

## Exercise: Square Brackets (2)

Square brackets can do more than just selecting columns. You can also use them to get rows, or observations, from a DataFrame. The following call selects the first five rows from the cars DataFrame:

```python
cars[0:5]
```

The result is another DataFrame containing only the rows you specified.

Pay attention: You can only select rows using square brackets if you specify a slice, like 0:4. Also, you're using the integer indexes of the rows here, not the row labels!


    Select the first 3 observations from cars and print them out.
    Select the fourth, fifth and sixth observation, corresponding to row indexes 3, 4 and 5, and print them out.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out first 3 observations
print(cars[0:3])

# Print out fourth, fifth and sixth observation
print(cars[3:6])

#Results

         cars_per_cap        country  drives_right
    US            809  United States          True
    AUS           731      Australia         False
    JPN           588          Japan         False
         cars_per_cap  country  drives_right
    IN             18    India         False
    RU            200   Russia          True
    MOR            70  Morocco          True
```

## Exercise: loc and iloc (1)

With loc and ilocyou can do practically any data selection operation on DataFrames you can think of. loc is label-based, which means that you have to specify rows and columns based on their row and column labels. iloc is integer index based, so you have to specify rows and columns by their integer index like you did in the previous exercise.

Try out the following commands to experiment with loc and iloc to select observations. Each pair of commands here gives the same result.

```python
cars.loc['RU']
cars.iloc[4]

cars.loc[['RU']]
cars.iloc[[4]]

cars.loc[['RU', 'AUS']]
cars.iloc[[4, 1]]
```

As before, code is included that imports the cars data as a Pandas DataFrame.


    Use loc or iloc to select the observation corresponding to Japan as a Series. The label of this row is JPN, the index is 2. Make sure to print the resulting Series.
    Use loc or iloc to select the observations for Australia and Egypt as a DataFrame. You can find out about the labels/indexes of these rows by inspecting cars. Make sure to print the resulting DataFrame.


## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out observation for Japan
print(cars.loc['JPN'])

# Print out observations for Australia and Egypt
print(cars.loc[['AUS', 'EG']])

#Results

    cars_per_cap      588
    country         Japan
    drives_right    False
    Name: JPN, dtype: object
         cars_per_cap    country  drives_right
    AUS           731  Australia         False
    EG             45      Egypt          True
```

## Exercise: loc and iloc (2)

loc and iloc also allow you to select both rows and columns from a DataFrame. To experiment, try out the following commands. Again, paired commands produce the same result.

```python
cars.loc['IN', 'cars_per_cap']
cars.iloc[3, 0]

cars.loc[['IN', 'RU'], 'cars_per_cap']
cars.iloc[[3, 4], 0]

cars.loc[['IN', 'RU'], ['cars_per_cap', 'country']]
cars.iloc[[3, 4], [0, 1]]
```


    Print out the drives_right value of the row corresponding to Morocco (its row label is MOR)
    Print out a sub-DataFrame, containing the observations for Russia and Morocco and the columns country and drives_right.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out drives_right value of Morocco
print(cars.loc['MOR', 'drives_right'])

# Print sub-DataFrame
print(cars.loc[['RU', 'MOR'], ['country', 'drives_right']])

#Results

    True
         country  drives_right
    RU    Russia          True
    MOR  Morocco          True
```

## Exercise: loc and iloc (3)

It's also possible to select only columns with loc and iloc. In both cases, you simply put a slice going from beginning to end in front of the comma:

```python
cars.loc[:, 'country']
cars.iloc[:, 1]

cars.loc[:, ['country','drives_right']]
cars.iloc[:, [1, 2]]
```


    Print out the drives_right column as a Series using loc or iloc.
    Print out the drives_right column as a DataFrame using loc or iloc.
    Print out both the cars_per_cap and drives_right column as a DataFrame using loc or iloc.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out drives_right column as Series
print(cars.loc[:, 'drives_right'])

# Print out drives_right column as DataFrame
print(cars.loc[:, ['drives_right']])

# Print out cars_per_cap and drives_right as DataFrame
print(cars.loc[:, ['cars_per_cap', 'drives_right']])

#Results

    US      True
    AUS    False
    JPN    False
    IN     False
    RU      True
    MOR     True
    EG      True
    Name: drives_right, dtype: bool
         drives_right
    US           True
    AUS         False
    JPN         False
    IN          False
    RU           True
    MOR          True
    EG           True
         cars_per_cap  drives_right
    US            809          True
    AUS           731         False
    JPN           588         False
    IN             18         False
    RU            200          True
    MOR            70          True
    EG             45          True
```
# Logic, Control Flow and Filtering

Comparison operators are operators that can tell how two Python values relate, and result in a boolean.

Among those was bool, short for boolean. Do you remember the bmi array from the intro course? Here it is again. Using the greater than sign, we could find out which values in bmi were above 23. Next, I used the resulting Boolean array to actually select that value. In this video, we'll dive a little deeper into the world of comparison operators, like this greater than sign. Comparison operators are operators that can tell how two Python values relate, and result in a boolean.

![image](https://github.com/user-attachments/assets/6fe18386-45b8-4413-bc0b-2cce8a463fa9)

## Exercise: Equality

To check if two Python values, or variables, are equal you can use ==. To check for inequality, you need !=. As a refresher, have a look at the following examples that all result in True. Feel free to try them out.

```python
2 == (1 + 1)
"intermediate" != "python"
True != False
"Python" != "python"
```
When you write these comparisons in a script, you will need to wrap a print() function around them to see the output.

    Write code to see if True equals False.
    Write Python code to check if -5 * 15 is not equal to 75.
    Ask Python whether the strings "pyscript" and "PyScript" are equal.
    What happens if you compare booleans and integers? Write code to see if True and 1 are equal.

## Solution

```python
# Comparison of booleans
True == False

# Comparison of integers
-5 * 15 != 75

# Comparison of strings
"pyscript" != "PyScript" 

# Compare a boolean with an integer
True == 1
```

## Exercise: Greater and less than

In the video, Hugo also talked about the less than and greater than signs, < and > in Python. You can combine them with an equals sign: <= and >=. Pay attention: <= is valid syntax, but =< is not.

All Python expressions in the following code chunk evaluate to True:

```python
3 < 4
3 <= 4
"alpha" <= "beta"
```

Remember that for string comparison, Python determines the relationship based on alphabetical order.

    Write Python expressions, wrapped in a print() function, to check whether:
        x is greater than or equal to -10. x has already been defined for you.
        "test" is less than or equal to y. y has already been defined for you.
        True is greater than False.


## Solution

```python
# Comparison of integers
x = -3 * 6
print(x >= -10)

# Comparison of strings
y = "test"
print("test" <= y)

# Comparison of booleans
print(True > False)

#Results
False
True
True
```

## Exercise: Compare arrays

Out of the box, you can also use comparison operators with NumPy arrays.

Remember areas, the list of area measurements for different rooms in your house from Introduction to Python? This time there's two NumPy arrays: my_house and your_house. They both contain the areas for the kitchen, living room, bedroom and bathroom in the same order, so you can compare them.

    Using comparison operators, generate boolean arrays that answer the following questions:
        
        Which areas in my_house are greater than or equal to 18?
        You can also compare two NumPy arrays element-wise. Which areas in my_house are smaller than the ones in your_house?
        Make sure to wrap both commands in a print() statement so that you can inspect the output!


## Solution

```python
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than or equal to 18
print(my_house >= 18)

# my_house less than your_house
print(my_house < your_house)

#Results
    [ True  True False False]
    [False  True  True False]
```

## Exercise: Boolean operators with NumPy

Before, the operational operators like < and >= worked with NumPy arrays out of the box. Unfortunately, this is not true for the boolean operators and, or, and not.

To use these operators with NumPy, you will need np.logical_and(), np.logical_or() and np.logical_not(). Here's an example on the my_house and your_house arrays from before to give you an idea:

```python
np.logical_and(my_house > 13, 
               your_house < 15)
```

    Generate boolean arrays that answer the following questions:
    Which areas in my_house are greater than 18.5 or smaller than 10?
    Which areas are smaller than 11 in both my_house and your_house? Make sure to wrap both commands in print() statement, so that you can inspect the output.

## Solution

```python
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than 18.5 or smaller than 10
print(np.logical_or(my_house > 18.5, my_house < 10))

# Both my_house and your_house smaller than 11
print(np.logical_and(my_house < 11, your_house < 11))

#Results
    [False  True False  True]
    [False False  True False]
```

## Exercise: if

It's time to take a closer look around in your house.

Two variables are defined in the sample code: room, a string that tells you which room of the house we're looking at, and area, the area of that room.
    
    Examine the if statement that prints out "looking around in the kitchen." if room equals "kit".
    Write another if statement that prints out "big place!" if area is greater than 15.

## Solution

```python
# Define variables
room = "kit"
area = 14.0

# if statement for room
if room == "kit" :
    print("looking around in the kitchen.")

# if statement for area
if area > 15:
    print("big place!")

#Results
looking around in the kitchen.
```

## Exercise: Add else

In the script, the if construct for room has been extended with an else statement so that "looking around elsewhere." is printed if the condition room == "kit" evaluates to False.

Can you do a similar thing to add more functionality to the if construct for area?

    Add an else statement to the second control structure so that "pretty small." is printed out if area > 15 evaluates to False.

## Solution
```python
# Define variables
room = "kit"
area = 14.0

# if-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
else :
    print("looking around elsewhere.")

# if-else construct for area
if area > 15 :
    print("big place!")
else :
    print("pretty small.")

#Result
    looking around in the kitchen.
    pretty small.
```

## Exercise: Customize further: elif

It's also possible to have a look around in the bedroom. The sample code contains an elif part that checks if room equals "bed". In that case, "looking around in the bedroom." is printed out.

It's up to you now! Make a similar addition to the second control structure to further customize the messages for different values of area.

    Add an elif to the second control structure such that "medium size, nice!" is printed out if area is greater than 10.

## Solution

```python
# Define variables
room = "bed"
area = 14.0

# if-elif-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
elif room == "bed":
    print("looking around in the bedroom.")
else :
    print("looking around elsewhere.")

# if-elif-else construct for area
if area > 15 :
    print("big place!")
elif area > 10:
    print("medium size, nice!")
else :
    print("pretty small.")

#Result
looking around in the bedroom.
medium size, nice!
```

Suppose you now want to keep the countries, so the observations in this case, for which the area is greater than 8 million square kilometers. There are three steps to this. First of all, we want to get the area column from brics. Next, we perform the comparison on this column and store its result. Finally, we should use this result to do the appropriate selection on the DataFrame.

![image](https://github.com/user-attachments/assets/c709cab7-d2ee-46dd-80cf-1db3484aa1e2)

![image](https://github.com/user-attachments/assets/9acf691a-82c9-45e5-ae9e-a7a1b53b98fd)

![image](https://github.com/user-attachments/assets/a3f1e5f7-c270-4fa4-8ae8-38be4581542e)

![image](https://github.com/user-attachments/assets/5be177c0-6b77-4576-91c2-df9e1200e069)

![image](https://github.com/user-attachments/assets/d7d3a271-519d-4794-9243-c8c37cc941ad)

![image](https://github.com/user-attachments/assets/541c94b7-c322-4363-9ef5-7a77a1e79575)

## Exercise: Driving right (1)

Remember that cars dataset, containing the cars per 1000 people (cars_per_cap) and whether people drive right (drives_right) for different countries (country)? The code that imports this data in CSV format into Python as a DataFrame is included in the script.

In the video, you saw a step-by-step approach to filter observations from a DataFrame based on boolean arrays. Let's start simple and try to find all observations in cars where drives_right is True.

drives_right is a boolean column, so you'll have to extract it as a Series and then use this boolean Series to select observations from cars.

    Extract the drives_right column as a Pandas Series and store it as dr.
    Use dr, a boolean Series, to subset the cars DataFrame. Store the resulting selection in sel.
    Print sel, and assert that drives_right is True for all observations.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Extract drives_right column as Series: dr
dr = cars['drives_right']

# Use dr to subset cars: sel
sel = cars[dr]

# Print sel
print(sel)

#Results
     cars_per_cap        country  drives_right
US            809  United States          True
RU            200         Russia          True
MOR            70        Morocco          True
EG             45          Egypt          True
```
You're getting full rows because you're using boolean indexing with the dr Series. When you do sel = cars[dr], pandas interprets dr as a boolean mask. It selects only the rows from the cars DataFrame where the corresponding value in dr is True.

It shows only results with True because of how boolean indexing works in pandas. The expression cars[dr] acts as a filter. It selects rows from the cars DataFrame where the corresponding element in the dr Series is True. Rows where the corresponding element in dr is False are excluded from the resulting DataFrame.

Think of dr as a mask that overlays the cars DataFrame. Where dr has True, the corresponding row in cars is "visible" and included in the result. Where dr has False, the row is "hidden" and excluded. Only the "visible" rows (those corresponding to True in dr) are included in the final output. This is a fundamental and efficient way to filter data in pandas.

Just to check dr

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Extract drives_right column as Series: dr
dr = cars['drives_right']

# Use dr to subset cars: sel
#sel = cars[dr]

# Print sel
print(dr)

#Results
US      True
AUS    False
JPN    False
IN     False
RU      True
MOR     True
EG      True
Name: drives_right, dtype: bool
```

You're getting a boolean Series because the 'drives_right' column in your cars.csv file contains boolean (True/False) values. When you extract this column using dr = cars['drives_right'], pandas creates a pandas Series object. A pandas Series is essentially a one-dimensional labeled array capable of holding any data type, and in this case, it's holding boolean data. The Name: drives_right, dtype: bool part of the output confirms this: the Series is named 'drives_right', and its data type (dtype) is boolean.

## Exercise: Driving right (2)

The code in the previous example worked fine, but you actually unnecessarily created a new variable dr. You can achieve the same result without this intermediate variable. Put the code that computes dr straight into the square brackets that select observations from cars.

    Convert the code to a one-liner that calculates the variable sel as before.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Convert code to a one-liner
sel = cars[cars['drives_right']]

# Print sel
print(sel)

#Results
     cars_per_cap        country  drives_right
US            809  United States          True
RU            200         Russia          True
MOR            70        Morocco          True
EG             45          Egypt          True
```

## Exercise: Cars per capita (1)

Let's stick to the cars data some more. This time you want to find out which countries have a high cars per capita figure. In other words, in which countries do many people have a car, or maybe multiple cars.

Similar to the previous example, you'll want to build up a boolean Series, that you can then use to subset the cars DataFrame to select certain observations. If you want to do this in a one-liner, that's perfectly fine!


    Select the cars_per_cap column from cars as a Pandas Series and store it as cpc.
    Use cpc in combination with a comparison operator and 500. You want to end up with a boolean Series that's True if the corresponding country has a cars_per_cap of more than 500 and False otherwise. Store this        boolean Series as many_cars.
    Use many_cars to subset cars, similar to what you did before. Store the result as car_maniac.
    Print out car_maniac to see if you got it right.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Create car_maniac: observations that have a cars_per_cap over 500
cpc = cars['cars_per_cap']
many_cars = cpc > 500
car_maniac = cars[many_cars]

# Print car_maniac
print(car_maniac)

#Results
     cars_per_cap        country  drives_right
US            809  United States          True
AUS           731      Australia         False
JPN           588          Japan         False
```

## Exercise: Cars per capita (2)

Remember about np.logical_and(), np.logical_or() and np.logical_not(), the NumPy variants of the and, or and not operators? You can also use them on Pandas Series to do more advanced filtering operations.

Take this example that selects the observations that have a cars_per_cap between 10 and 80. Try out these lines of code step by step to see what's happening.

```python
cpc = cars['cars_per_cap']
between = np.logical_and(cpc > 10, cpc < 80)
medium = cars[between]
```


    Use the code sample provided to create a DataFrame medium, that includes all the observations of cars that have a cars_per_cap between 100 and 500.
    Print out medium.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Import numpy, you'll need this
import numpy as np

# Create medium: observations with cars_per_cap between 100 and 500
cpc = cars['cars_per_cap']
between=np.logical_and(cpc > 100, cpc < 500)
medium = cars[between]

# Print medium
print(medium)

#Results
    cars_per_cap country  drives_right
RU           200  Russia          True
```

# Loops

The while loop is somewhat similar to an if statement: it executes the code inside if the condition is True. However, as opposed to the if statement, the while loop will continue to execute this code over and over again as long as the condition is true.

## Exercise: Basic while loop

Below you can find the example from the video where the error variable, initially equal to 50.0, is divided by 4 and printed out on every run:

```python
error = 50.0
while error > 1 :
    error = error / 4
    print(error)
```

This example will come in handy, because it's time to build a while loop yourself! We're going to code a while loop that implements a very basic control system for an inverted pendulum. If there's an offset from standing perfectly straight, the while loop will incrementally fix this offset.

Note that if your while loop takes too long to run, or your session is expiring, you might have created an infinite loop. In particular, remember to indent the contents of the loop using four spaces or auto-indentation, and make sure the conditions are such that the loop has a stopping point.

    Create the variable offset with an initial value of 8.
    Code a while loop that keeps running as long as offset is not equal to 0. Inside the while loop:
        Print out the sentence "correcting...".
        Next, decrease the value of offset by 1. You can do this with offset = offset - 1.
        Finally, still within your loop, print out offset so you can see how it changes.

## Solution

```python
# Initialize offset
offset=8

# Code the while loop
while offset != 0 :
    offset = offset - 1
    print("correcting...")

#Results
    correcting...
    correcting...
    correcting...
    correcting...
    correcting...
    correcting...
    correcting...
    correcting...
```

## Exercise: Add conditionals

The while loop that corrects the offset is a good start, but what if offset is negative? You can try to run the following code where offset is initialized to -6:

```python
# Initialize offset
offset = -6

# Code the while loop
while offset != 0 :
    print("correcting...")
    offset = offset - 1
    print(offset)
```

but your session will be disconnected. The while loop will never stop running, because offset will be further decreased on every run. offset != 0 will never become False and the while loop continues forever.

Fix things by putting an if-else statement inside the while loop.

    Initialize offset to -6.
    Inside the while loop, complete the if-else statement:
    If offset is greater than zero, you should decrease offset by 1.
    Else, you should increase offset by 1.
    
If your code is taking too long to run (or your session is expiring), you probably made a mistake. Check your code and make sure that the statement offset != 0 will eventually evaluate to FALSE!

## Solution

```python
# Initialize offset
offset = -6

# Code the while loop
while offset != 0 :
    print("correcting...")
    if offset > 0 :
      offset=offset - 1
    else : 
      offset=offset + 1  
    print(offset)

#Results
    correcting...
    -5
    correcting...
    -4
    correcting...
    -3
    correcting...
    -2
    correcting...
    -1
    correcting...
    0
```

Next to the while loop, Python features another type of loop as well: You've seen the while loop and now it's time for another loop: the for loop! 

![image](https://github.com/user-attachments/assets/38d6c56d-a12c-4263-8f4f-56cb2aa19c47)

## Exercise: Loop over a list

Have another look at the for loop that Hugo showed in the video:

```python
fam = [1.73, 1.68, 1.71, 1.89]
for height in fam : 
    print(height)
```

As usual, you simply have to indent the code with 4 spaces to tell Python which code should be executed in the for loop.

The areas variable, containing the area of different rooms in your house, is already defined.

    Write a for loop that iterates over all elements of the areas list and prints out every element separately.

## Solution

```python
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Code the for loop
for area in areas:
    print(area)

#Results
    11.25
    18.0
    20.0
    10.75
    9.5
```

## Exercise: Indexes and values (1)

Using a for loop to iterate over a list only gives you access to every list element in each run, one after the other. If you also want to access the index information, so where the list element you're iterating over is located, you can use enumerate().

As an example, have a look at how the for loop from the video was converted:

```python
fam = [1.73, 1.68, 1.71, 1.89]
for index, height in enumerate(fam) :
    print("person " + str(index) + ": " + str(height))
```

    Adapt the for loop in the sample code to use enumerate() and use two iterator variables.
    Update the print() statement so that on each run, a line of the form "room x: y" should be printed, where x is the index of the list element and y is the actual list 
    element, i.e. the area. Make sure to print out this exact string, with the correct spacing.

## Solution

```python
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Change for loop to use enumerate() and update print()
for index, area in enumerate(areas) :
    print("room " + str(index) + ": " + str(area))

#Results
room 0: 11.25
room 1: 18.0
room 2: 20.0
room 3: 10.75
room 4: 9.5
```

## Exercise: Indexes and values (2)

For non-programmer folks, room 0: 11.25 is strange. Wouldn't it be better if the count started at 1?

    Adapt the print() function in the for loop so that the first printout becomes "room 1: 11.25", the second one "room 2: 18.0" and so on.


## Solution

```python
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Code the for loop
for index, area in enumerate(areas) :
    print("room " + str(index+1) + ": " + str(area))

#Results
    room 1: 11.25
    room 2: 18.0
    room 3: 20.0
    room 4: 10.75
    room 5: 9.5
```

## Exercise: Loop over list of lists

Remember the house variable from the Intro to Python course? Have a look at its definition in the script. It's basically a list of lists, where each sublist contains the name and area of a room in your house.

It's up to you to build a for loop from scratch this time!

    Write a for loop that goes through each sublist of house and prints out the x is y sqm, where x is the name of the room and y is the area of the room.


## Solution

```python
# house list of lists
house = [["hallway", 11.25], 
         ["kitchen", 18.0], 
         ["living room", 20.0], 
         ["bedroom", 10.75], 
         ["bathroom", 9.50]]
         
# Build a for loop from scratch
for room, area in (house) :
    print("the " + str(room) + " is " + str(area) + " sqm")

#Results
    the hallway is 11.25 sqm
    the kitchen is 18.0 sqm
    the living room is 20.0 sqm
    the bedroom is 10.75 sqm
    the bathroom is 9.5 sqm
```

## Exercise: Loop over dictionary

In Python 3, you need the items() method to loop over a dictionary:

```python
world = { "afghanistan":30.55, 
          "albania":2.77,
          "algeria":39.21 }

for key, value in world.items() :
    print(key + " -- " + str(value))
```

Remember the europe dictionary that contained the names of some European countries as key and their capitals as corresponding value? Go ahead and write a loop to iterate over it!

    Write a for loop that goes through each key:value pair of europe. On each iteration, "the capital of x is y" should be printed out, where x is the key and y is the value of the pair.

## Solution

```python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw', 'austria':'vienna' }
          
# Iterate over europe

for key, value in europe.items() :
    print("the capital of "+ key + " is " + str(value))

#Results
    the capital of spain is madrid
    the capital of france is paris
    the capital of germany is berlin
    the capital of norway is oslo
    the capital of italy is rome
    the capital of poland is warsaw
    the capital of austria is vienna
```

## Exercise: Loop over NumPy array

If you're dealing with a 1D NumPy array, looping over all elements can be as simple as:

```python
for x in my_array :
    ...
```

If you're dealing with a 2D NumPy array, it's more complicated. A 2D array is built up of multiple 1D arrays. To explicitly iterate over all separate elements of a multi-dimensional array, you'll need this syntax:

```python
for x in np.nditer(my_array) :
    ...
```

Two NumPy arrays that you might recognize from the intro course are available in your Python session: np_height, a NumPy array containing the heights of Major League Baseball players, and np_baseball, a 2D NumPy array that contains both the heights (first column) and weights (second column) of those players.


    Import the numpy package under the local alias np.
    Write a for loop that iterates over all elements in np_height and prints out "x inches" for each element, where x is the value in the array.
    Write a for loop that visits every element of the np_baseball array and prints it out.


## Solution

```python
# Import numpy as np
import numpy as np

# For loop over np_height
for x in np_height :
    print(str(x) + " inches")

# For loop over np_baseball
for x in np.nditer(np_baseball) :
    print(x)

#Results
74 inches
74 inches
72 inches
74
74
72
```

There's one killer data structure out there that we haven't covered up to now when it comes to looping: the Pandas DataFrame. 

## Exercise: Loop over DataFrame (1)

Iterating over a Pandas DataFrame is typically done with the iterrows() method. Used in a for loop, every observation is iterated over and on every iteration the row label and actual row contents are available:

```python
for lab, row in brics.iterrows() :
    ...
```

In this and the following exercises you will be working on the cars DataFrame. It contains information on the cars per capita and whether people drive right or left for seven countries in the world.

    Write a for loop that iterates over the rows of cars and on each iteration perform two print() calls: one to print out the row label and one to print out all of the rows contents.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Iterate over rows of cars
for lab, row in cars.iterrows() :
    print(lab)
    print(row)

#Results
US
cars_per_cap              809
country         United States
drives_right             True
Name: US, dtype: object
AUS
cars_per_cap          731
country         Australia
drives_right        False
Name: AUS, dtype: object
JPN
cars_per_cap      588
country         Japan
drives_right    False
Name: JPN, dtype: object
IN
cars_per_cap       18
country         India
drives_right    False
Name: IN, dtype: object
RU
cars_per_cap       200
country         Russia
drives_right      True
Name: RU, dtype: object
MOR
cars_per_cap         70
country         Morocco
drives_right       True
Name: MOR, dtype: object
EG
cars_per_cap       45
country         Egypt
drives_right     True
Name: EG, dtype: object
```

## Exercise: Loop over DataFrame (2)

The row data that's generated by iterrows() on every run is a Pandas Series. This format is not very convenient to print out. Luckily, you can easily select variables from the Pandas Series using square brackets:

```python
for lab, row in brics.iterrows() :
    print(row['country'])
```


    Using the iterators lab and row, adapt the code in the for loop such that the first iteration prints out "US: 809", the second iteration "AUS: 731", and so on.
    The output should be in the form "country: cars_per_cap". Make sure to print out this exact string (with the correct spacing).
        You can use str() to convert your integer data to a string so that you can print it in conjunction with the country label.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Adapt for loop
for lab, row in cars.iterrows() :
    print(lab + ": " + str(row['cars_per_cap']))

#Results
US: 809
AUS: 731
JPN: 588
IN: 18
RU: 200
MOR: 70
EG: 45
```

## Exercise: Add column (1)

In the video, Hugo showed you how to add the length of the country names of the brics DataFrame in a new column:

```python
for lab, row in brics.iterrows() :
    brics.loc[lab, "name_length"] = len(row["country"])
```

You can do similar things on the cars DataFrame.


    Use a for loop to add a new column, named COUNTRY, that contains a uppercase version of the country names in the "country" column. You can use the string method upper() for this.
    To see if your code worked, print out cars. Don't indent this code, so that it's not part of the for loop.

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Code for loop that adds COUNTRY column
for lab, row in cars.iterrows() :
    cars.loc[lab, "COUNTRY"] = row["country"].upper()

# Print cars
print(cars)

#Results
     cars_per_cap        country  drives_right        COUNTRY
US            809  United States          True  UNITED STATES
AUS           731      Australia         False      AUSTRALIA
JPN           588          Japan         False          JAPAN
IN             18          India         False          INDIA
RU            200         Russia          True         RUSSIA
MOR            70        Morocco          True        MOROCCO
EG             45          Egypt          True          EGYPT
```

## Exercise: Add column (2)

Using iterrows() to iterate over every observation of a Pandas DataFrame is easy to understand, but not very efficient. On every iteration, you're creating a new Pandas Series.

If you want to add a column to a DataFrame by calling a function on another column, the iterrows() method in combination with a for loop is not the preferred way to go. Instead, you'll want to use apply().

Compare the iterrows() version with the apply() version to get the same result in the brics DataFrame:

```python
for lab, row in brics.iterrows() :
    brics.loc[lab, "name_length"] = len(row["country"])

brics["name_length"] = brics["country"].apply(len)
```

We can do a similar thing to call the upper() method on every name in the country column. However, upper() is a method, so we'll need a slightly different approach:


    Replace the for loop with a one-liner that uses .apply(str.upper). The call should give the same result: a column COUNTRY should be added to cars, containing an uppercase version of the country names.
    As usual, print out cars to see the fruits of your hard labor

## Solution

```python
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Use .apply(str.upper)
cars["COUNTRY"] = cars["country"].apply(str.upper)
print(cars)

#Results
         cars_per_cap        country  drives_right        COUNTRY
    US            809  United States          True  UNITED STATES
    AUS           731      Australia         False      AUSTRALIA
    JPN           588          Japan         False          JAPAN
    IN             18          India         False          INDIA
    RU            200         Russia          True         RUSSIA
    MOR            70        Morocco          True        MOROCCO
    EG             45          Egypt          True          EGYPT
```

# Case Study: Hacker Statistics

![image](https://github.com/user-attachments/assets/2a0c4503-25d1-45d0-8e3a-448512054536)

![image](https://github.com/user-attachments/assets/0ff05ea5-8da1-40ad-9870-5476f688322f)


## Exercise: Random float

Randomness has many uses in science, art, statistics, cryptography, gaming, gambling, and other fields. You're going to use randomness to simulate a game.

All the functionality you need is contained in the random package, a sub-package of numpy. In this exercise, you'll be using two functions from this package:

    seed(): sets the random seed, so that your results are reproducible between simulations. As an argument, it takes an integer of your choosing. If you call the function, no output will be generated.
    rand(): if you don't specify any arguments, it generates a random float between zero and one.


Import numpy as np.
Use seed() to set the seed; as an argument, pass 123.
Generate your first random float with rand() and print it out.

## Solution

```python
# Import numpy as np
import numpy as np

# Set the seed
np.random.seed(123)

# Generate and print random float
x = np.random.rand()
print(x)

#Results

0.6964691855978616
```

## Exercise: Roll the dice

In the previous exercise, you used rand(), that generates a random float between 0 and 1.

As Hugo explained in the video you can just as well use randint(), also a function of the random package, to generate integers randomly. The following call generates the integer 4, 5, 6 or 7 randomly. 8 is not included.

```python
import numpy as np
np.random.randint(4, 8)
```

NumPy has already been imported as np and a seed has been set. Can you roll some dice?


    Use randint() with the appropriate arguments to randomly generate the integer 1, 2, 3, 4, 5 or 6. This simulates a dice. Print it out.
    Repeat the outcome to see if the second throw is different. Again, print out the result.

## Solution

```python
# Import numpy and set seed
import numpy as np
np.random.seed(123)

# Use randint() to simulate a dice
print(np.random.randint(1,7))

# Use randint() again
print(np.random.randint(1,7))

#Results

6
3
```
## Exercise: Determine your next move

In the Empire State Building bet, your next move depends on the number you get after throwing the dice. We can perfectly code this with an if-elif-else construct!

The sample code assumes that you're currently at step 50. Can you fill in the missing pieces to finish the script? numpy is already imported as np and the seed has been set to 123, so you don't have to worry about that anymore.


    Roll the dice. Use randint() to create the variable dice.
    Finish the if-elif-else construct by replacing ___:
    If dice is 1 or 2, you go one step down.
    if dice is 3, 4 or 5, you go one step up.
    Else, you throw the dice again. The number on the dice is the number of steps you go up.
    Print out dice and step. Given the value of dice, was step updated correctly?


## Solution

```python
# NumPy is imported, seed is set

# Starting step
step = 50

# Roll the dice
dice = np.random.randint(1,7) #random integer between 1 (inclusive) and 7 (exclusive), so the possible outcomes are 1, 2, 3, 4, 5, and 6

# Finish the control construct
if dice <= 2 :
    step = step - 1
elif dice <= 5 :
    step = step + 1
else :
    step = step + np.random.randint(1,7) #If the dice roll is 6, step is incremented by another random integer between 1 and 6

# Print out dice and step
print(dice)
print(step)

#Results
6
53
```

