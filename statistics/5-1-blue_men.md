[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Python Code**  
```{python}
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
fiveten = dist.cdf(177.8)
sixone = dist.cdf(185.4)
diff = round((sixone - fiveten) * 100, 2)
print("""The percentage of the US male population that is between 5'10" and 6'1" is {}%""".format(diff))
```

**Results**  
Based off the Python code above, it can be calculated the percentage of the US male population that is between 5'10" and 6'1" is 34.21%
