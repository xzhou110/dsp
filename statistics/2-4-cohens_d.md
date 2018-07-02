[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

import nsfg
import math

df = nsfg.ReadFemPreg()

#pregordr is a column
pregordr = df['pregordr']

#clean the datasets. Fix incorrect data and formats
df=nsfg.CleanFemPreg(df)



import thinkstats2
import thinkplot

''' plot a historgram
hist = thinkstats2.Hist([1, 2, 2, 3, 5])
thinkplot.Hist(hist)
thinkplot.Show(xlabel='value', ylabel='frequency')
'''

#The expression in brackets is a boolean Series that selects rows from the DataFrame and returns a new DataFrame.
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

'''
hist = thinkstats2.Hist(live.birthwgt_lb, label='birthwgt_lb')
thinkplot.Hist(hist)
thinkplot.Show(xlabel='pounds', ylabel='frequency')
'''

#create dataframe for first baby and other babies
firsts=live[live.birthord==1]
others=live[live.birthord!=1]

'''
#plot 2 historgrams side by side
first_hist = thinkstats2.Hist(firsts.prglngth)
other_hist = thinkstats2.Hist(others.prglngth)
width = 0.45
#each bar width=0.45
thinkplot.PrePlot(2)
thinkplot.Hist(first_hist, align='right', width=width)
thinkplot.Hist(other_hist, align='left', width=width)
thinkplot.Show(xlabel='weeks', ylabel='frequency',xlim=[27, 46])
#show data between 27 and 46 weeks
'''

mean=live.prglngth.mean()
var = live.prglngth.var()
std = live.prglngth.std()


#define CoheneffectSize
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d


cohen_prglngth=CohenEffectSize(firsts['prglngth'],others['prglngth'])
cohen_totalwgt=CohenEffectSize(firsts['totalwgt_lb'], others['totalwgt_lb'])

print('Difference of prglngth is ' +str(cohen_prglngth))
print('Difference of totalweight is '+str(cohen_totalwgt))
