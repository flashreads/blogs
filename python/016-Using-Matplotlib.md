---
id: 016-using-matplotlib.md
title: How to make an easy plot with matplotlib
tags: python, beginner, plot
author: Marlene Heinrich
meta-description: Using matplotlib to create scientific plots
---

## What is matplotlib?

Matplotlib is a package that can be used to create plots or different form of
visualization of data.

## Creating a simple 2d-Plot

As a firs step the package needs to be imported with:

```python
from matplotlib import pyplot as plt
```

Now we create the data we want to plot, so for example:
```python
x = [1, 2, 3, 4, 5, 6]
y = [1, 0, 3.5, 3, 2, 1]
```

To plot this data we need a simple command:
```python
plt.scatter(x, y, marker = 'x', color='red')
plt.show()
```
The scatter-function gives a simple representation of the datapoints and the
show-command is needed to actually see the plot.

To create a scientifically acceptable result some improvement has to be done:
```python
plt.title('Testplot') #Adds a title above the plot
plt.xlabel('x') #Add labels to the axis
plt.ylabel('y')
plt.grid(linestyle='dotted') #Add a major grid
plt.errorbar(x, y, xerr=0.1, yerr=0.1, marker='x', linewidth=0, elinewidth=1)
plt.show()
plt.savefig('testplot.pdf') #Save the plot as a PDF
```
A difference one should note, is that in this case we have used the
errorbar-function. Both, to plot and to add errorbars. Because of this the
linewidth had to be set to zero otherwise the points would have a connection
line. To still have errorbars the elinewidth hat to be set to something greater
zero, otherwise they would just disappear.

With just slight changes a lot of plots can be done using python!
