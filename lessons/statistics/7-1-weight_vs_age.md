[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

**Using data from the NSFG for birth weight and mother’s age:**
```Python
live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])
```
_Scatter plot of birth weight versus mother’s age:_
```Python
def ScatterPlot(ages, weights, alpha=1.0):
    thinkplot.Scatter(ages, weights, alpha=alpha)
    thinkplot.Config(xlabel='age (years)',
                     ylabel='weight (lbs)',
                     xlim=[10, 45],
                     ylim=[0, 15],
                     legend=False)
ScatterPlot(live.agepreg, live.totalwgt_lb, alpha=1.0)
```
_Pearson’s and Spearman’s correlations:_
```Python
def Corr(xs, ys):
    xs = np.asarray(xs)
    ys = np.asarray(ys)

    meanx, varx = thinkstats2.MeanVar(xs)
    meany, vary = thinkstats2.MeanVar(ys)

    corr = Cov(xs, ys, meanx, meany) / np.sqrt(varx * vary)
    return corr
Corr(live.agepreg, live.totalwgt_lb) #Pearson’s correlation
#Output
0.06883397035410908 #correlation is positive

def SpearmanCorr(xs, ys):
    xranks = pd.Series(xs).rank()
    yranks = pd.Series(ys).rank()
    return Corr(xranks, yranks)
SpearmanCorr(live.agepreg, live.totalwgt_lb)
#Output
0.09461004109658226 #magnitude is less than 0.3 has little if any (linear) correlation
```


