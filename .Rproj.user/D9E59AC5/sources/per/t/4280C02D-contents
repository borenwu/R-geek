library(quantmod)
library(PerformanceAnalytics)

getSymbols(c('IBM','GE','AAPL','^GSPC'),src='yahoo',from='2010-01-01')
names(IBM) <- c("open",'high','low','close','volume','adjusted')
names(GE) <- c("open",'high','low','close','volume','adjusted')
names(AAPL) <- c("open",'high','low','close','volume','adjusted')
names(GSPC) <- c("open",'high','low','close','volume','adjusted')

dat = merge(IBM$adjusted,GE$adjusted,AAPL$adjusted,GSPC$adjusted)
names(dat) = c('IBM','GE','AAPL','SP500')


IBM_ret=dailyReturn(IBM)  
GE_ret=dailyReturn(GE)
AAPL_ret = dailyReturn(AAPL)
SP500_ret=dailyReturn(GSPC)
dat_ret = merge(IBM_ret,GE_ret,AAPL_ret,SP500_ret)
names(dat_ret) = c('IBM','GE','AAPL','SP500')

Rf <-0.04/12

results <- table.AnnualizedReturns(dat_ret,Rf=Rf)

table.Stats(dat_ret)

chart.Bar(dat_ret[,1], main="IBM Daily Returns")
chart.Bar(monthlyReturn(IBM), main="IBM Monthly Returns")
chart.CumReturns(dat_ret,main="Total Returns",legend.loc="topleft")
chart.Correlation(dat_ret, histogram=TRUE, pch="+")


CAPM.alpha(dat_ret[,1:3],dat_ret[,4],Rf=Rf)
CAPM.beta(dat_ret[,1:3],dat_ret[,4],Rf=Rf)