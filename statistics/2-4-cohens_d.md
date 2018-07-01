[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Python Code** 
```{python}
import nsfg
import math

def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d


df = nsfg.ReadFemPreg()
nsfg.CleanFemPreg(df)
first_df = df.where(df['pregordr'] == 1)
first_df = first_df.dropna(subset = ['pregordr'])
other_df = df.where(df['pregordr'] != 1)
other_df = other_df.dropna(subset = ['pregordr'])

weight_effect = CohenEffectSize(first_df['totalwgt_lb'], other_df['totalwgt_lb'])
length_effect = CohenEffectSize(first_df['prglngth'], other_df['prglngth'])

print("""Cohen's d for weight between the first borns and the rest is {}. \n
      Cohen's d for pregnancy length between first borns and the rest is {}.""".format(weight_effect, length_effect))
```
**Results**  
When running the above code, the Cohen's *d* statistic that we would get between first borns and the rest of the births in terms of birth weight is -0.0313. If we calculate the same thing but for pregnancy length, the Cohen's *d* statisic is -0.0691. Thus, we can see that the effect size of birth weight with respect to birth order is greater than that of pregnancy length to birth order.
