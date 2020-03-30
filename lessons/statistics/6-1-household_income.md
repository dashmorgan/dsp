[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

**Computation of median, mean, skewness and Pearson’s skewness of income.**
_(Provided fanction InterpolateSample(df, log_upper=6.0) from thinkstats2 for income sampling gives an error, so I read data as:_
```Python
import hinc
income_df = hinc.ReadData()

income_df = income_df['income'][0:41]#exclude inf value from the column
```
For calculation were used functions:
```Python
def Mean(xs):
    return RawMoment(xs, 1)
def Skewness(xs):
    return StandardizedMoment(xs, 3)
def PearsonMedianSkewness(xs):
    median = Median(xs)
    mean = RawMoment(xs, 1)
    var = CentralMoment(xs, 2)
    std = np.sqrt(var)
    gp = 3 * (mean - median) / std
    return gp
def Median(xs):
    cdf = thinkstats2.Cdf(xs)
    return cdf.Value(0.5)
```
Result:
```Python
Mean(income_df)
#output
106096.56097560975
Median(income_df)
#output
104999.0
PearsonMedianSkewness(income_df)
#output
0.05364285463874303
Skewness(income_df)
#output
0.16240652683317236 #positive skewness indicates that a distribution skews right
