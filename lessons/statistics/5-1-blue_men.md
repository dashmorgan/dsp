[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Percentage of the U.S. male population is in range between 5'10" and 6'1".**<br>
The distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men.<br>
5'10" and 6'1" in cm are 177.8 and 185.928, respectively.<br>
By using function 
```Python
def EvalNormalCdf(x, mu=mu, sigma=sigma):
    return scipy.stats.norm.cdf(x, loc=mu, scale=sigma)
```
We evaluate how many male population are above 177.8 and 185.928 as such:
```Python
a = EvalNormalCdf(177.8, mu=mu, sigma=sigma)
b = EvalNormalCdf(185.928, mu=mu, sigma=sigma)
print("a: ", round(a,2))
print("b: ", round(b,2))
#Output
a:  0.49
b:  0.85
```
Then by calculating the difference between values **b** and **a**, 
```Python
round(b-a,2)
#Output
0.36
```
We find that about 36% of male population is in range between 5'10" and 6'1".


