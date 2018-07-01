[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

**Python Code**  
```{python}
import thinkplot
import nsfg

resp = nsfg.ReadFemResp()

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf

# Create and plot the unbiased distribution
resp_pmf = thinkstats2.Pmf(resp['numkdhh'], label = 'numkdhh')
thinkplot.PrePlot(1)
thinkplot.Pmf(resp_pmf)
thinkplot.Config(xlabel='Number of Children', ylabel='PMF')
thinkplot.show()

# Create and plot the biased distribution
bias_pmf = BiasPmf(resp_pmf, 'Biased')
thinkplot.PrePlot(2)
thinkplot.Pmfs([resp_pmf, bias_pmf])
thinkplot.Config(xlabel='Number of Children', ylabel='PMF')
thinkplot.show()

# Calculating means
unbiased_mean = resp_pmf.Mean()
biased_mean = bias_pmf.Mean()
print("Unbiased Mean: {}\nBiased_mean: {}".format(unbiased_mean, biased_mean))
```

**Results**  
From running the above Python code, we can calculate the unbiased mean would be 1.02, while the biased mean would be 2.04.
