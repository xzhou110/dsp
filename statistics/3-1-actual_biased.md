[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

import nsfg
import math
import thinkstats2
import thinkplot


#calculate probability

def Normalize (hist):

    n=hist.Total()
    d={}
    for x, freq in hist.items():
        d[x]=freq/n
    return d


'''
# plot the charts and show
pmf = thinkstats2.Pmf([1, 2, 2, 3, 5])

thinkplot.PrePlot(2, cols=2)
thinkplot.Hist(first_pmf, align='right', width=width)
thinkplot.Hist(other_pmf, align='left', width=width)
thinkplot.Config(xlabel='weeks',
ylabel='probability', axis=[27, 46, 0, 0.6])
thinkplot.PrePlot(2)
thinkplot.SubPlot(2)
thinkplot.Pmfs([first_pmf, other_pmf])
thinkplot.Show(xlabel='weeks',
 axis=[27, 46, 0, 0.6])


# zoom in the differece and produce the chart
weeks = range(35, 46)
diffs = []
for week in weeks:
    p1 = first_pmf.Prob(week)
    p2 = other_pmf.Prob(week)
    diff = 100 * (p1 - p2)
    diffs.append(diff)
thinkplot.Bar(weeks, diffs)
'''
#define biased probability
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
        new_pmf=Normalize(new_pmf)

    return new_pmf

#define inverse of biased probability
def UnbiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    
    for x, p in pmf.Items():
        new_pmf.Mult(x, 1.0/x)
        new_pmf=Normalize(new_pmf)

        #new_pmf.Normalize()
        
    return new_pmf

'''
# show both actual and biased plot together
biased_pmf = BiasPmf(pmf, label='observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Show(xlabel='class size', ylabel='PMF')
'''

resp = nsfg.ReadFemResp()
numkdhh=resp['numkdhh']
hist = thinkstats2.Hist(numkdhh, label='numkdhh')
n = hist.Total()
pmf = hist.Copy()
for x, freq in hist.Items():
    pmf[x] = freq / n

biased_pmf=BiasPmf(pmf, 'unbiased')

#plot the biased and unbiased grapth
biased_pmf = BiasPmf(pmf, label='observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Show(xlabel='class size', ylabel='PMF')
