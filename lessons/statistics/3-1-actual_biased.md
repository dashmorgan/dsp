[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

### Number of children under 18 in the household (NUMKDHH)
**_(Actual calculations were made in Jupyter Notebook)_**
```Python
hist = thinkstats2.Hist(preg.outcome, label=' NUMKDHH') #making a dictionary of number of children and its prequencies
n = hist.Total()
d = {}
for x, freq in hist.Items():
    d[x] = freq
d 
{1: 9148, 4: 1921, 2: 1862, 6: 352, 5: 190, 3: 120} #dictionary output

pmf = thinkstats2.Pmf(d, label='actual') #creating a dictionary that maps from each value (num of children) to its probability     using pmf class provided by thinkstats2
def BiasPmf(pmf, label): #defining a function for calculating "biased" probability 
    new_pmf = pmf.Copy(label=label)
    for x, p in pmf.Items(): 
        new_pmf.Mult(x, x)
    new_pmf.Normalize() 
    return new_pmf #returning a new dictionary
biased_pmf = BiasPmf(pmf, label='observed') 
#plotting the actual and observed distributions
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf]) 
thinkplot.Show(xlabel='NUMKDHH', ylabel='PMF')
<Figure size 576x432 with 0 Axes>
print('mean', pmf.Mean()) #printing a mean of actual NUMKDHH
mean 1.763996174501582
print('mean', biased_pmf.Mean()) #printing a mean of biased of NUMKDHH
mean 2.7456001334556674
```
Mean of actual NUMKDHH is lower then mean of biased NUMKDHH, which means that:<br> children,<br> _who being asked how many kids under 18 (including themselves) are in their household,_<br> think that their household has more children then it actually has.

