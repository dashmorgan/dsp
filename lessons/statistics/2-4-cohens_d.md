[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

<b>(Done in Jupyter notebook):</b>

```python  
import thinkstats2 #importing module
from nsfg import ReadFemPreg #importing function that reads the NSFG pregnancy data
preg = ReadFemPreg() #reads pregnancy data and partitions first babies and others.
live = preg[preg.outcome == 1] #DataFrames (all live births, first babies, others)
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
d = thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
print("Cohen's d: ", d)
```  
<b>Output:</b><br>
<b>Cohen's d:</b>  -0.088672927072602

<b>Result:</b>

Computed Cohen's d = -0.08867 suggests that first babies are slighter lighter then others. 

The difference in means is 0.08867 standard deviations, which is small (Cohen' d less then 0.2 considers as 'small' effect size).
  
