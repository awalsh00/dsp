# [Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

## Question

In the [BRFSS](https://www.cdc.gov/brfss/annual_data/annual_2008.htm), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.

In order to [join Blue Man Group](http://bluemancasting.com), you have to be male between 5'10" and 6'1". What percentage of the U.S. male population is in this range?

_Hint: use scipy.stats.norm.cdf_

[[Link Test of stuff|ts2]]

## Answer

### Code

```python
import sys
import scipy.stats

# Generate a normal distribution model of male heights in cm
modeled = scipy.stats.norm(loc=178,scale=7.7)

#Convert heights to cm and calculate the percentage
min_height = (5*12+10)*2.54
max_height = (6*12+1)*2.54
pr = modeled.cdf(max_height) - modeled.cdf(min_height)

# Display the results
print('Males between ~', round(min_height,ndigits=2),'cm and ~', sep='', end='')
print(round(max_height,ndigits=2),'cm represent ~',round(pr*100,ndigits=2),'% of the population',sep='')
```

### Output

```
Males between ~177.8cm and ~185.42cm represent ~34.27% of the population
```