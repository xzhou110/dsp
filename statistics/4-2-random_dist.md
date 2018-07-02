[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

import numpy as np
import thinkstats2
import thinkplot



#generate 1000 random numbers
rand=[]
rand=np.random.random_sample(1000)

cdf=thinkstats2.Cdf(rand, label='random_numbers')
pmf=thinkstats2.Pmf(rand, label='random_numbers')

thinkplot.Cdf(cdf)
thinkplot.Show(xlable='value', ylabel='CDF')

thinkplot.Pmf(pmf)
thinkplot.Show(xlable='value', ylabel='PMF')
