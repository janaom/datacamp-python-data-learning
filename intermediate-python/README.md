# Intermediate Python

Learning Python is crucial for any aspiring data science practitioner. Learn to visualize real data with Matplotlib’s functions and get acquainted with data structures such as the dictionary and pandas DataFrame. This four-hour intermediate course will help you to build on your existing Python skills and explore new Python applications and functions that expand your repertoire and help you work more efficiently.

You'll discover how dictionaries offer an alternative to Python lists, and why the pandas dataframe is the most popular way of working with tabular data. In the second chapter of this course, you’ll find out how you can create and manipulate datasets, and how to access them using these structures. Hands-on practice throughout the course will build your confidence in each area.

As you progress, you’ll look at logic, control flow, filtering and loops. These functions work to control decision-making in Python programs and help you to perform more operations with your data, including repeated statements. You’ll finish the course by applying all of your new skills by using hacker statistics to calculate your chances of winning a bet.

Once you’ve completed all of the chapters, you’ll be ready to apply your new skills in your job, new career, or personal project, and be prepared to move onto more advanced Python learning.

----------

✅ Matplotlib

✅ Dictionaries & Pandas

✅ Logic, Control Flow and Filtering

✅ Loops

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

# Solution

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
#Results

2100

10.85

![image](https://github.com/user-attachments/assets/d7c9edc3-fd85-4806-99c7-91a224601955)
