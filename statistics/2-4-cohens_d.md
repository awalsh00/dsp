# [Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

## Question

Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen's d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

## Answer

### Code

```python
import sys
import numpy as np

# `ts2` is a sym-link to the `thinkstats2/code` directory (for me: `~ds/metis/metisgh/prework/ThinkStats2/code`)
# This allows us to `import` that code, and the imports in that code to work
sys.path.append('ts2')
import nsfg

def cohensd(x1,x2):
    '''Return the cohen d of the two sets provided'''
    
    i=len(x1)
    j=len(x2)
    
    square_s1 = np.var(x1)
    square_s2 = np.var(x2)
    
    s = np.sqrt((square_s1*i + square_s2*j)/(i+j))
    
    d = (x1.mean()-x2.mean())/s
    
    return d


# Ingest the NSFG data
preg = nsfg.ReadFemPreg(dct_file='ts2/2002FemPreg.dct', dat_file='ts2/2002FemPreg.dat.gz')
live = preg[preg.outcome == 1]
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

# Calculate Cohen's d for totalwgt_lb and prglngth
cohensd_wgt = cohensd(firsts.totalwgt_lb,others.totalwgt_lb)
cohensd_lng = cohensd(firsts.prglngth,others.prglngth)

# Display the results in a grid for comparision
print('Function','Total Weight','Pregnancy Length',sep='\t\t')
print('First babies mean:',firsts.totalwgt_lb.mean(),firsts.prglngth.mean(),sep='\t')
print('Other babies mean:',others.totalwgt_lb.mean(),others.prglngth.mean(),sep='\t')
print("\tCohen's d:",cohensd_wgt,cohensd_lng,sep='\t')
```

### Output

```
Function		Total Weight			Pregnancy Length
First babies mean:	7.201094430437772		38.60095173351461
Other babies mean:	7.325855614973262		38.52291446673706
	Cohen's d:	-0.08868274594713024		0.028882209288160925
```

The **Cohen's d** for total weight is _3x_ larger than it is for length.
