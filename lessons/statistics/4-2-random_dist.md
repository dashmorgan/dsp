[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

**(Using Python Jupyter Notebook)**
<br>
_Generating 1000 numbers by using **random.random**:
```Python
num = np.random.random(1000)
```
Numbers generated are uniform.<br>
_Plotting PMF (Probability mass function):_
```Python
num_pmf = thinkstats2.Pmf(num, label='num pmf') 
thinkplot.Pmf(num_pmf)
thinkplot.Config(xlabel='Random 1000 numbers', ylabel='Pmf', loc='upper right')
```
The Graph resulted from plotting PMF of Random 1000 numbers is difficult to read since all numbers have same probability and the effect of random noise increases.<br> PMF works well if the number of values is small.<br>
<br>
_Plotting CDF (Cumulative distribution functions):_
```Python
cdf = thinkstats2.Cdf(num, label='1000 random numbers')
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='1000 random numbers)', ylabel='CDF', loc='upper left')
```
The Gragh resulted from the plotting CDF is more apparent then plot of PMF, since CDF maps values to its percentile rank.
