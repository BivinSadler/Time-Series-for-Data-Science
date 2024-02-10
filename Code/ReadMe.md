<img src="https://github.com/BivinSadler/Time-Series-for-Data-Science/blob/main/TS%20for%20DS.jpeg" height="300" class="center" >

# R Code Page Number for Time Series for Data Science:  

### Pages 12-13  
```r
data(dfw.2011)  
dfw.2011  
plot(dfw.2011)  
plot(dfw.2011,type= 'l')  
```

### Page 14  
```r
dfw.2011.ts = ts(dfw.2011,start= c(2011,1),frequency= 12)  
dfw.2011.ts  
plot(dfw.2011.ts)  
class(dfw.2011.ts)  
```

### Page 15  
```r
data(lynx)  
plot(lynx)  
class(lynx)  
lynx  
```

### Page 16  
```r
dfw.2011.num = as.numeric(dfw.2011.ts)  
class(dfw.2011.num)  
dfw.2011.num  
```

### Page 16-17  
```r
x = c(10,20,30,40,50,60,70,80,90,100,110,120,130,140,150,160,170)  
xTSmonth = ts(x,start = c(2018,6),frequency = 12)  
xTSmonth  
xTSweek = ts(x,start = c(1,4),frequency = 7)  
xTSweek  
window(xTSweek,start = c(2,1),end = c(2,7))  
```

### Page 18  
```r
data(AirPassengers)   
window(AirPassengers,start = c(1950,1),end = c(1950,12))  
data(lynx)  
log.lynx= log(lynx)  
\# Note that log.lynx retains the ts file information contained in file lynx  
plotts.wge(log.lynx)  
```

### Page 20  
```r
AirPassengersData = read.csv("Your file location// AirPassengers.csv",header = TRUE)  
```

### Page 21  
```r
s1= scan("Your file location// Sample1.txt")  
s2= scan("Your file location// Sample2.txt")  
```

### Page 28  
```r
data(ozona)  
ozona.ts= ts(ozona$CFS_Sold)  
plot(ozona.ts,type= 'o',xlab= 'Day')  
```

### Page 29-30  
```r
data(bitcoin)  
# Linear interpolation with one missing value   
bitcoin[162]=bitcoin[161]+(bitcoin[163]-bitcoin[161])/2  
# Linear interpolation with two adjacent missing values  
bitcoin[165]=bitcoin[164]+(bitcoin[167]-bitcoin[164])/3  
bitcoin[166]=bitcoin[164]+2*(bitcoin[167]-bitcoin[164])/3  
```

### Page 43
```r
data(tesla)
tesla.3= ma.smooth.wge(tesla,order= 3,plot= FALSE)
tesla.8= ma.smooth.wge(tesla,order= 8,plot= FALSE)
plot(tesla)
plot(tesla.3$smooth)
plot(tesla.8$smooth)
# the plots based on the tswge ts object dfw.yr are obtained analogously
```

### Page 44
```r
set.seed(6946)
t= 1:60
cosine= cos(2*pi*t/ 10)
line= - 2+ .05*t
z= rnorm(n= 60,sd= 1)
x= cosine+ line+ z
plot(x)
ma.smooth.wge(x,order= 5)
```


### Page 45
```r
data(sunspot2.0.month)
data(sunspot2.0)
sunspot2.0.1749= window(sunspot2.0,start= 1749,end= 2020)
ss.yr= aggregate(sunspot2.0.month,FUN= mean)
```

### Page 46
```r
data(sunspot2.0)
data(sunspot2.0.month)
sunspot2.0.12= ma.smooth.wge(sunspot2.0.month,order= 12,plot= FALSE)
sunspot2.0.sm12= ts(sunspot2.0.12$smooth,start= c(1749,1),
frequency= 12)
par(mfrow= c(2,2))
plotts.wge(sunspot2.0.1749)
plotts.wge(ss.yr)
plotts.wge(sunspot2.0.month)
plotts.wge(sunspot2.0.sm12)
```


### Page 48   Note:  This code replaces the incorrect code on ### Page 48

```r
data(tx.unemp.unadj)
tx.unemp.sm= ma.smooth.wge(tx.unemp.unadj,order= 12, plot= FALSE)
tx.unemp.sm12= ts(tx.unemp.sm$smooth,start= c(2000,1),frequency= 12)
plotts.wge(tx.unemp.sm12)
```


### Page 51
```r
data(AirPassengers)
logAirPassengers= log(AirPassengers)
logair.12= ma.smooth.wge(logAirPassengers,order= 12)
logair.sm12= ts(logair.12$smooth,start= c(1949,1),frequency= 12)
```

### Page 51
```r
data(AirPassengers)
logAirPassengers= log(AirPassengers)
logair.12= ma.smooth.wge(logAirPassengers,order= 12)
logair.sm12= ts(logair.12$smooth,start= c(1949,1),frequency= 12)

seas.logair= logAirPassengers- logair.sm12
round(seas.logair,4) # rounding to 4 decimal places for listing below
```



### Page 52
```r
# convert the ts file to a vector
seas.logair.numeric= as.numeric(seas.logair) # convert ts file to a vector
# convert this vector to a matrix with ncol= number of years
seas.logair.matrix= matrix(seas.logair.numeric,ncol= 12) #12 years and 12 months
```


### Page 53
```r
seas.logair.matrix.t= t(seas.logair.matrix)

months= colMeans(seas.logair.matrix.t, na.rm= TRUE)
round(months,4)

seas.means= rep(months,12) # replicates the 12 monthly means for each year (12)
seas.means= ts(seas.means,start= c(1949,1),frequency= 12)

logair.noise= logAirPassengers- logair.sm12- seas.means
```

### Page 54  Note:  This code corrects the incorrect code on ### Page 54
```r
data(tx.unemp.unadj)
tx.unemp.sm= ma.smooth.wge(tx.unemp.unadj,order= 12,plot= FALSE)
tx.unemp.sm12= ts(tx.unemp.sm$smooth,start= c(2000,1), frequency= 12)
plotts.wge(tx.unemp.sm12)
```

### Pages 54-55
```r
seas.tx.unemp= tx.unemp.unadj- tx.unemp.sm12
seas.tx.unemp.numeric= as.numeric(seas.tx.unemp) #convert ts file to a vector
# convert this vector to a matrix with ncol= number of years
seas.tx.unemp.matrix= matrix(seas.tx.unemp.numeric,ncol= 20) # 20 years
seas.tx.unemp.matrix.t= t(seas.tx.unemp.matrix) # transpose matrix
months= colMeans(seas.tx.unemp.matrix.t,na.rm= TRUE) # colMeans are monthly means
seas.means= rep(months,20) # replicates the 12 monthly means
tx.unemp.noise= tx.unemp.unadj- tx.unemp.sm12- seas.means
```

### Page 56
```r
AirPass.sm12= ma.smooth.wge(AirPassengers,order= 12)
AirPass.sm12= ts(AirPass.sm12$smooth,start= c(1949,1),frequency= 12)

seas.AirPass= AirPassengers/ AirPass.sm12
```



### Page 57
```r
seas.AirPass.numeric= as.numeric(seas.AirPass) #convert ts file to a vector
# convert this vector to a matrix with ncol= number of years
seas.AirPass.matrix= matrix(seas.AirPass.numeric,ncol= 12) # 12 years
seas.AirPass.matrix.t= t(seas.AirPass.matrix) # transpose matrix
months= colMeans(seas.AirPass.matrix.t,na.rm= TRUE) # colMeans are monthly means
seas.means= rep(months,12) # replicates the 12 monthly means for each year (12)
seas.means= ts(seas.means,start= c(1949,1),frequency= 12)

Air.Pass.noise= AirPassengers/ (AirPass.sm12*seas.means)
```

### Page 58  Note: We have included  the three lines to calculate seas.means because seas.means was the name we  used for both AirPassengers and Texas Unemployment data
```r
months=colMeans(seas.tx.unemp.matrix.t, na.rm=TRUE)
seas.means=rep(months,20)  # replicates the 12 monthly means for each year (12)
seas.means=ts(seas.means,start=c(2000,1),frequency=12)
tx.unemp.adj.1 = tx.unemp.unadj - seas.means
```

### Page 59
```r
library(seasonal) # assuming that "seasonal" has been installed
census= seas(tx.unemp.unadj)
# the seasonally adjusted data are in the ts file census$data[,3]
```

### Page 60
```r
# this code is included to compute the correct seasonal means
months= colMeans(seas.logair.matrix.t, na.rm= TRUE)
round(months,4)
#
seas.means= rep(months,12) # replicates the 12 monthly means for each year (12)
seas.means= ts(seas.means,start= c(1949,1),frequency= 12)

AirPassengers.adj = AirPassengers/ seas.means
library(seasonal) # assuming that seasonal has been installed
census= seas(AirPassengers)
# the seasonally adjusted data are in the ts file census$data[,3]
```

### Page 62
```r
data(wtcrude2020)
wtc36= window(wtcrude2020,start= c(2018,1))
wtc36= as.numeric(wtc36)
ma5= ma.pred.wge(wtc36,order= 5,k.ahead= 4)
```


### Page 65
```r
wtc36.exp= exp.smooth.wge(wtc36,alpha= .4,n.ahead= 4)
```


### Page 66
```r
data(dfw.yr)
exp.smooth.wge(dfw.yr,alpha= .2,n.ahead= 10)
```


### Page 68
```r
# Figure 2.20(a)
ap.hw= HoltWinters(AirPassengers,seasonal= "mult")
plot(ap.hw)
# Figure 2.20(b)
ap.pred= predict(ap.hw,n.ahead= 36)
plot(ap.hw,ap.pred,lty= 1:2)
```


### Page 69
```r
AP9= window(AirPassengers,start= c(1949,1),end= c(1957,12))
AP9.hw= HoltWinters(AP9,seasonal= "mult")
AP9.pred= predict(AP9.hw,n.ahead= 36)
plot(AirPassengers,type= 'l')
points(AP9.pred,type= 'l',lty= 2)
```

### Page 93
```r
x10= c(40,27,35,34,31,27,26,34,37,47)
x15= c(27,48,49,33,51,39,48,42,46,31)
cor.x10x15= cor(x10,x15)
```

### Page 124
```r
data(lynx)
llynx= log10(lynx)
x3= gen.arma.wge(n= 100,phi= c(1.75,- .95),sn= 203)
par(mfrow= c(1,3),mar= c(4,3,.2,.5))
plotts.wge(sunspot2.0)
plotts.wge(llynx)
plotts.wge(x3)
```

### Page 126
```r
t= 1:100
y= rep(0,100)
y1= rep(0,100)
y2= rep(0,100)
y3= rep(0,100)
for(i in 1:100){y1[i] = 4*sin(2*pi*.04*i)}
for(i in 1:100){y2[i] = 1.25*sin(2*pi*.125*i+ 1)}
for(i in 1:100){y3[i] = .5*sin(2*pi*.25*i+ 2.5)}
y= y1+ y2+ y3
par(mfrow= c(2,2),mar= c(4,2.5,1.5,.5))
plot(y,type= 'l',xlab= '(a) Linear Combination of Sines',ylim=c(-6,6))
plot(y1,type= 'l',xlab= '(b) Component 1',ylim=c(-6,6))
plot(y2,type= 'l',xlab= '(c) Component 2',ylim=c(-6,6))
plot(y3,type= 'l',xlab= '(d) Component 3',ylim=c(-6,6))
```


### Page 129
```r
t= 1:1000
tm= t/ 200
y1= sin(2*pi*.2*tm)
z1= sin(2*pi*1.2*tm)
tp= c(0,1,2,3,4,5)
yp= sin(2*pi*.2*tp)
par(mfrow= c(1,1),mar= c(2.5,2.5,1,1.5))
plot(tm,y1,type= 'l',xlab= 'Time',xlim= c(0,5))
points(tm,z1,type= 'l',lwd= 2)
points(tp,yp,pch= 19)
```

### Page 133
```r
x= gen.arma.wge(n= 200,phi= c(0.1300,1.4414,- 0.0326,- 0.8865),sn= 9310)
# this generates an AR(4) realization (details in Chapter 5)
par(mfrow= c(2,3))
plotts.wge(x)
abline(v= 100)
sample.spec.wge(x[1:100])
sample.spec.wge(x)
parzen.wge(x)
parzen.wge(x,trunc= 8)
parzen.wge(x,trunc= 175)
```


### Page 135
```r
x= gen.arma.wge(n= 200,phi= c(0.1300,1.4414,- 0.0326,- 0.8865),sn= 9310)
# this generates an AR(4) realization (details in Chapter 5)
plotts.sample.wge(x)
```


### Page 136
```r
y1= rep(0,100)
y2= rep(0,100)
y3= rep(0,100)
y= rep(0,100)
for(t in 1:100){y1[t] = 4*sin(2*pi*.04*t)}
for(t in 1:100){y2[t] = 1.25*sin(2*pi*.125*t+ 1)}
for(t in 1:100){y3[t] = .5*sin(2*pi*.25*t+ 2.5)}
y= y1+ y2+ y3
par(mfrow= c(1,3))
plotts.wge(y)
parzen.wge(y,trunc= 20)
parzen.wge(y,trunc= 30)
```


### Page 138
```r
data(sunspot2.0)
plotts.sample.wge(sunspot2.0)

data(llynx)
plotts.sample.wge(llynx)
```



### Page 141
```r
# Note: This code is for WT Crude from Jan 1990 through December 2020
data(wtcrude2020)
n= length(wtcrude2020)
parz.wt= parzen.wge(wtcrude2020,plot= FALSE)
s9= ma.smooth.wge(wtcrude2020,order= 9,plot= FALSE)
parz.s9= parzen.wge(s9$smooth[5:114],plot= FALSE)
d1.wt= rep(NA,n)
for(t in 2:n) d1.wt[t- 1]= wtcrude2020[t] - wtcrude2020[t- 1]
parz.d1= parzen.wge(d1.wt[1:n- 1],plot= FALSE)
par(mfrow= c(1,3),mar= c(4.5,3,2,.5))
plot(wtcrude2020,type= 'l',xlab= '(a) WT Crude Oil Price')
plot(s9$smooth,type= 'l',xlab= '(b) WT Crude Smoothed')
plot(d1.wt,type= 'l',xlab= '(c) WR Crude Differenced data',ylim= c(- 50,50))
```



### Page 142
```r
x= gen.arma.wge(n= 200,phi= c(0.1300,1.4414,- 0.0326,- 0.8865),sn= 9310)
n= length(x)
par(mfrow= c(3,2),mar= c(3,2.5,1,1.5))
plot(x,type= 'l',ylim= c(- 20,20))
parzen.wge(x)
s6= ma.smooth.wge(x,order= 6,plot= FALSE)
plot(s6$smooth,type= 'l',ylim= c(- 20,20))
parzen.wge(s6$smooth[4:197])
for(t in 2:n) d1[t- 1]= x[t] - x[t- 1]
plot(d1,type= 'l',ylim= c(- 20,20))
parzen.wge(d1[1:n- 1])
```

### Page 143  Note:  the last line should be parzen.wge(high$x.filt) instead of parzenww.wge(high$x.filt) which is in the text
```r
par(mfrow= c(3,2),mar= c(3,2.5,1,1.5))
plot(x,type= 'l',ylim= c(- 20,20))
parzen.wge(x)
low= butterworth.wge(x,type= 'l',cutoff= .25,plot= FALSE)
plot(low$x.filt,type= 'l',ylim= c(- 20,20))
parzen.wge(low$x.filt)
high= butterworth.wge(x,type= 'h',cutoff= .25,plot= FALSE)
plot(high$x.filt,type= 'l',ylim= c(- 20,20))
parzen.wge(high$x.filt)
```


### Page 157
```r
plotts.true.wge(phi= .9,plot.data= FALSE)
plotts.true.wge(phi= .7,plot.data= FALSE)
```



### Page 158
```r
x= gen.arma.wge(n= 150,phi= .9,sn= 20)
plotts.sample.wge(x)

x= gen.arma.wge(n= 150,phi= .7,sn= 130)
plotts.sample.wge(x)
```


### Page 159
```r
gen.arma.wge(n= 150,phi= .95,sn= 305)
gen.arma.wge(n= 150,phi= .99,sn= 404)
```


### Page 161
```r
plotts.true.wge(n= 100,phi= - .7,plot.data= FALSE)
x= gen.arma.wge(n= 150,phi= - .7,sn= 878)
plotts.sample.wge(x)
```

### Page 162
```r
x= gen.arima.wge(n= 150, d= 1,sn= 734)

a= gen.arma.wge(n= 500,sn= 10,plot= FALSE) #generates 500 N(0,1) white noise
xx.spin= rep(0,500)
xx= rep(0,150)
for(i in 1:499) {xx.spin[i+ 1]= 1.1*xx.spin[i] + a[i]}
plot(xx[1:150])
xx[1:150]= xx.spin[350:499] # generates 500 and keeps the last 150
```


### Page 165
```r
unit.circle.wge(real= c(1.11,- 1.43),imaginary= c(0,0))
```

### Page 166
```r
unit.circle.wge(real= c(- 1.25,.67),imaginary= c(0,0))
```


### Page 167
```r
unit.circle.wge(real= c(1,1),imaginary= c(.5,- .5))
```

### Page 168
```r
plotts.true.wge(phi= c(.2,.63),plot.data= FALSE)
x= gen.arma.wge(n= 150,phi= c(.2,.63),sn= 13)
plotts.sample.wge(x)
```


### Page 170
```r
plotts.true.wge(phi= c(1.6,- .8),plot.data= FALSE)
x= gen.arma.wge(n= 150,phi= c(1.6,- .8),sn= 19)
plotts.sample.wge(x)
```

### Page 171
```r
plotts.true.wge(phi= c(- .5,- .8),plot.data= FALSE)
x= gen.arma.wge(n= 150,phi= c(- .5,- .8),sn= 19)
plotts.sample.wge(x)
```

### Page 172
```r
data(tswge)
plotts.wge(lynx)
llynx= log10(lynx)
plotts.sample.wge(llynx)
```


### Page 176
```r
x= gen.arma.wge(n= 200,phi= c(0.1300,1.4414,- .0326,- .8865),sn= 9310,plot= FALSE)
plotts.sample.wge(x)
```



### Page 180
```r
x= gen.arma.wge(n= 150,phi= c(1.95,- 1.85,.855),sn= 129,plot= FALSE)
plotts.sample.wge(x)
```



### Page 181
```r
xa= gen.arma.wge(n= 150,phi= c(1.8,- .96,0,.001),mu= 0,sn= 3233)
plotts.sample.wge(xa) # plots (a- c)

xd= gen.arma.wge(n= 150,phi= c(.8,- .94,0,.001),mu= 0,sn= 3233)
plotts.sample.wge(xd) # plots (d- f)

xg= gen.arma.wge(n= 150,phi= c(2.6,- 3.34,2.46,- .9024),mu= 0,sn= 3233)
plotts.sample.wge(xg) # plots (g- i)
```


### Page 183
```r
cf= mult.wge(fac1= c(1.8,- .95),fac2= - .6, fac3= c(0,- .8))

x= gen.arma.wge(n= 200,phi= cf$model.coef,sn= 10)

x1= gen.arma.wge(n= 200,phi= c(1.2,- .67,.39,.104,- .456),sn= 10)
```



### Page 185 
```r
A= gen.arma.wge(n= 150,phi= c(1.95,- 1.85,.855), sn= 3847)
plotts.sample.wge(A) # plots (a- c)

A_real= gen.arma.wge(n= 150,phi= c(1.71,- 1.22,.475), sn= 327)
plotts.sample.wge(A_real) # plots(d- f)

A_complex= gen.arma.wge(n= 150,phi= c(1.70,- 1.60,.63), sn= 2813)
plotts.sample.wge(A_complex) # plots(g- i)
```


### Page 191 
```r
psi.weights.wge(phi= c(1.6,- .8),lag.max= 5)
```


### Page 194 
```r
plotts.true.wge(phi= 0,theta= .99,lag.max= 25,vara= 1,plot.data= FALSE)

x= gen.arma.wge(n= 150,theta= .99,sn= 53)
plotts.sample.wge(x)
```


### Page 195 
```r
x= gen.arma.wge(n= 150,theta= - .8,sn= 363)
plotts.sample.wge(x)
```


### Page 197 
```r
ma2= plotts.true.wge(phi= 0,theta= c(.4,- .9),plot.data= FALSE)

x= gen.arma.wge(n= 150,theta= c(.4,- .9),sn= 65)
plotts.sample.wge(x)
```


### Page 199 
```r
pi.weights.wge(theta= c(.4,- .9),lag.max= 6)
```

### Page 202 
```r
pi.weights.wge(phi= c(1.6,- .8),theta= -.9,lag.max= 6)
```

### Page 204   Note:  the second instance of plots.sample.wge has the .wge left off in the text
```r
fig5.26a= gen.arma.wge(n= 150,phi= c(2.57,- 2.50,.92),sn= 65)
plotts.sample.wge(fig5.26a) # this plots Figure 5.26(a- c)

fig5.26d= gen.arma.wge(n= 150,phi= 0,theta= .92,sn= 65)
plotts.sample.wge(fig5.26d) # this plots Figure 5.26(d- f)

fig5.26g= gen.arma.wge(n= 150,phi= c(2.57,- 2.50,.92),,theta= .92,sn= 65)
plotts.sample.wge(fig5.26g) # this plots Figure 5.26(g- i)
```


### Page 207   Note:  the second instance of plotts.sample.wge has the .wge left off in the text
```r
fig5.27a= gen.arma.wge(n= 150,phi= .95,sn= 20)
plotts.sample.wge(fig5.27a) # this plots Figure 5.27(a- c)

fig5.27d= gen.arma.wge(n= 150,phi= .95,theta= .8,sn= 20)
plotts.sample.wge(fig5.27d) # this plots Figure 5.27 (d- f)
```



### Page 219  
```r
arma31= gen.arma.wge(n= 150,phi= c(2.57,- 2.50,.92),theta= .92,mu= 30,sn= 65)

est.arma.wge(arma31,p= 3,q= 1)
```

### Page 223  
```r
est.arma.wge(arma31,p= 3,q= 1)
```

### Page 224  
```r
par(mfrow= c(1,2))
a= gen.arma.wge(n= 150,phi= c(1.71,- 1.22,.475),sn= 327,plot= FALSE)
b= rev(a)
plotts.wge(a)
plotts.wge(b)
```


### Page 225  
```r
A_real= gen.arma.wge(n= 150,phi= c(1.71,- 1.22,.475),sn= 327)
A_real.ml= est.ar.wge(A_real,p= 3,type= 'mle')
# The command A_real.ml= est.ar.wge(A_real,p= 3) produces the same results
# since 'mle' is the default type.
```

### Page 226  
```r
A_real.yw= est.ar.wge(A_real,p= 3,method= 'yw')
A_real.burg= est.ar.wge(A_real,p= 3,method= 'burg')

ar4= gen.arma.wge(n= 100,phi= c(2.76,- 3.76,2.6,- .89),sn= 468)
plotts.sample.wge(ar4)
```

### Page 227
```r
ar4.ml= est.ar.wge(ar4,p= 4)
ar4.yw= est.ar.wge(ar4,p= 4,type= 'yw')
ar4.bg= est.ar.wge(ar4,p= 4,type= 'burg')
```

### Page 230
```r
x= gen.arma.wge(n= 150,phi= 0,theta= 0,sn= 147)
```


### Page 233
```r
aic.wge(x,p= 0:10,q= 0:4,type= 'aic')

aic.wge(x,p= 0:10,q= 0:0,type= 'aic')

arma31= gen.arma.wge(n= 150,phi= c(2.57,- 2.50,.92),theta= .92,mu= 30,sn= 65)
```

### Page 234
```r
a= aic.wge(arma31,p= 0:12, q= 0:4)

b= aic.wge(arma31,p= 0:12,q= 0:4,type= 'bic')
cc= aic.wge(arma31,p= 0:12,q= 0:4,type= 'aicc')

aic5.wge(arma31,p= 0:12,q= 0:4)
aic5.wge(arma31,p= 0:12,q= 0:4,type= 'aicc')
aic5.wge(arma31,p= 0:12,q= 0:4,type= 'bic')
```


### Page 236
```r
data(lynx)
llynx= log10(lynx)
aic5.wge(llynx,p= 0:12,q= 0:4)
aic5.wge(llynx,p= 0:12,q= 0:4,type= 'aicc')
aic5.wge(llynx,p= 0:12,q= 0:4,type= 'bic')
```


### Page 236  Note: In the text the gen.arma.wge statement is missing the theta=.92 part of the generated model
```r
arma31.500= gen.arma.wge(n= 500,phi= c(2.57,- 2.50,.92),theta= .92,mu= 30,sn= 65)

aic5.wge(arma31.500,p= 0:12, q= 0:4)
aic5.wge(arma31.500,p= 0:12, q= 0:4,type= 'bic')
aic5.wge(arma31.500,p= 0:12, q= 0:4,type= 'aicc')
```


### Page 240  
```r
A_real= gen.arma.wge(n= 150,phi= c(1.71,- 1.22,.475),sn= 327)

aic5.ar.wge(A_real,p= 0:12,type= 'bic',method= 'burg')
```


### Page 241  Note: aic.ar.wge should not have the q=0:4 parameters in the call statement.
```r
data(sunspot2.0)
ss= aic.ar.wge(sunspot2.0,p= 0:12)
ss

aic5.ar.wge(sunspot2.0,p= 0:12)

In Try This:
aic5.ar.wge(sunspot2.0,p= 0:20)
```

### Page 242
```r
aic5.ar.wge(sunspot2.0,p= 0:20,method= 'burg')

aic5.ar.wge(sunspot2.0,p= 0:20,type= 'bic')
```


### Pages 247-248
```r
x= c(14.0,14.8,14.0,14.0,13.8,12.4,12.9,11.9,12.0,10.9,10.5,9.2,10.7,11.3,
9.2,8.6,8.2,7.3,7.9,8.8)
aic.x= aic.wge(x,p= 0:4,q= 0:0) # aic.x$p is the value of p selected by AIC
# AIC picks p= 1
est.x= est.ar.wge(x,aic.x$p)
# the MLE of phi(1)= .92 (est.x$phi)
# white noise variance estimate is .82 (est.x$avar)
mean(x)
# the estimated mean is 11.12

fore.x= fore.arma.wge(x,est.x$phi,n.ahead= 20,limits= FALSE)
```

### Page 249
```r
y= c(40.3,36.6,40.1,42.4,40.7,38.5,39.3,42.0,41.5,39.3,37.8,40.4,43.5,41.5,37.4,
37.8,40.6,43.2,40.7,38.71,40.9,40.7,40.2,39.5,39.4)
# y is a time series of length n= 25
aic.y= aic.wge(y,p= 0:10,q= 0:0)
# AIC picks p= 2 so we estimate the parameters
est.y= est.ar.wge(y,aic.y$p)
# MLE in $phi: 0.30 - 0.90
# white noise variance estimate is $avar= .57
# sample mean is $xbar= 40.12

fore.y= fore.arma.wge(y,phi= est.y$phi,n.ahead= 20,limits= FALSE)
```

### Page 252
```r
arma21= gen.arma.wge(n= 100,phi= c(1.6,- .9),theta= .9,mu= 20,sn= 5789)

aic5.wge(arma21,p= 0:12,q= 0:4)

est21= est.arma.wge(arma21,p= 2,q= 1)
```


### Page 253
```r
fore.21= fore.arma.wge(arma21,phi= est21$phi,theta= est21$theta,n.ahead= 30,
limits= FALSE)
```


### Page 254
```r
data(sunspot2.0)
aic.ss= aic.wge(sunspot2.0,p= 0:10,q= 0:4)
est.ss= est.ar.wge(sunspot2.0,p= aic.ss$p) # aic selects p= 9
fore.ss= fore.arma.wge(sunspot2.0,phi= est.ss$phi,n.ahead= 30,limits= FALSE)
```


### Page 257
```r
fore.21= fore.arma.wge(arma21,phi= c(1.583,- .899),theta= .929,n.ahead= 30,
limits= TRUE,alpha= .05)
```

### Page 259
```r
v= true.arma.aut.wge(phi= c(1.583,- .899),theta= .929,vara= .8426)

data(sunspot2.0)
est.ss= est.ar.wge(sunspot2.0,p= 9)
```


### Page 260
```r
fore.ss= fore.arma.wge(sunspot2.0,phi= est.ss$phi,n.ahead= 30,limits= TRUE,
alpha= .05)
```

### Page 265
```r
data(sunspot2.0)
est.ss= est.ar.wge(sunspot2.0,p= 2)
fore.ss= fore.arma.wge(sunspot2.0,phi= est.ss$phi,n.ahead= 30,limits= TRUE)
```

### Page 269  Note:  The parameter specifying the ϕ_j  coefficients is phi,  not phis as is in the text. 
```r
est9 = est.arma.wge(sunspot2.0, p = 9, factor = FALSE)
roll.win.rmse.wge(sunspot2.0, phi = est9$phi, h = 10)
```


### Page 278
```r
plotts.true.wge(phi= .99999,plot.data= FALSE)

x010= gen.arima.wge(n= 100,d= 1,sn= 409)
plotts.sample.wge(x010)
```


### Page 279
```r
x9= gen.arma.wge(n= 10000,phi= .999,mu= 50,sn= 509)
x1= gen.arima.wge(n= 10000,d= 1,mu= 50,sn= 340)
```


### Page 280
```r
plotts.wge(x9[1:100])
plotts.wge(x1[1:100])
```


### Page 281
```r
x9.100= gen.arma.wge(n= 100,phi= .999,mu= 50,sn= 509)
x1.100= gen.arima.wge(n= 100,d= 1,mu= 50,sn= 340)
```


### Page 282  Note: In plotts.sample.wge on the last line there should be a comma after d1
```r
x010= gen.arima.wge(n= 100,d= 1,sn= 409)
d1= artrans.wge(x010,phi.tr= 1)

x010= gen.arima.wge(n= 100,d= 1,sn= 409,plot= FALSE)
d1= artrans.wge(x010,phi.tr= 1)
plotts.sample.wge(d1, arlimits=TRUE,speclimits=c(-20,10))
```


### Page 282  
```r
ar2= gen.arma.wge(n= 200,phi= c(1.3,- .65),sn= 637,plot= FALSE)
plotts.sample.wge(ar2)
```

### Page 284  
```r
x210= gen.arima.wge(n= 200,phi= c(1.3,- .65),d= 1,sn= 4855)
d1= artrans.wge(x210,phi.tr= 1)
# plot the data (first row) and the differenced data (second row)
plotts.sample.wge(x210)
plotts.sample.wge(d1)
```



### Page 285  
```r
x220= gen.arima.wge(n= 200,phi= c(1.3,- .65),d= 2,sn= 450)

d1= artrans.wge(x220,phi.tr= 1)
d2= artrans.wge(d1,phi.tr= 1)
# or
d2= artrans.wge(x220,phi.tr= c(2,- 1))
```


### Page 286
```r
x220= gen.arima.wge(n= 200,phi= c(1.3,- .65),d= 2,sn= 450)
d1= artrans.wge(x220,phi.tr= 1,plot= FALSE)
d2= artrans.wge(d1,phi.tr= 1,plot= FALSE)
plotts.sample.wge(x220)
plotts.sample.wge(d1)
plotts.sample.wge(d2)
```


### Page 289
```r
x010= gen.arima.wge(n= 100,d= 1,sn= 409)

h.kpss= ur.kpss(x010,type= 'mu',lags= 'short')

1-1.3704B+0.7264B^2    0.9433+-0.6978i      0.8523       0.1014
```


### Page 292-294   Note:  The correct fitted ARIMA(2,1,0) model is (1-1.37B+.73B^2)(1-B)X_t=a_t,    where σ ̂_a^2=1.036.
```r
x010= gen.arima.wge(n= 100,d= 1,sn= 409)
d1= artrans.wge(x010,phi.tr= 1)

x210= gen.arima.wge(n= 200,phi= c(1.3,- .65),d= 1,sn= 4855)
d1= artrans.wge(x210,phi.tr= 1)
aic.wge(d1,p= 0:10,q= 0:2)
est.ar.wge(d1,p= 2)

x220= gen.arima.wge(n= 200,phi= c(1.3,- .65),d= 2,sn= 450)
d1= artrans.wge(x220,phi.tr= 1)
d2= artrans.wge(d1,phi.tr= 1)
aic.wge(d2,p= 0:10,q= 0:2)
est.ar.wge(d2,p= 2)
```


### Page 294   Note:  The plotts.sample.wge code below is correct.  The text has an extra arlimits=TRUE
```r
data(dow1985)
plotts.sample.wge(dow1985)
ddow= artrans.wge(dow1985,phi.tr= 1,plot= FALSE)
plotts.sample.wge(ddow,arlimits= TRUE,speclimits=c(-10,10))
```


### Page 296
```r
d1= artrans.wge(dow1985,phi.tr= 1)   
```


### Page 297-298   Note:  last two lines should have d2.pop in place of d2
Also, as of 7/14/22 uspop in tswge is incorrect
```r
data(uspop)
uspop/1000000
d1.pop= artrans.wge(uspop,phi.tr= 1)
d2.pop= artrans.wge(d1.pop,phi.tr= 1)
aic.wge(d2.pop,p= 0:10,q= 0:4)
aic.wge(d2.pop,p= 0:10,q= 0:4,type= 'bic')
```

### Page 297-298   
```r
x010= gen.arima.wge(n= 150,d= 1,sn= 409)
fore.010= fore.arima.wge(x010[1:100],d= 1,n.ahead= 50,limits= FALSE)
```

### Page 300
```r
psi.weights.wge(phi= 1,lag.max= 50)

par(mfrow= c(1,3))
t= 1:150
plot(t[1:100],x010[1:100],xlim= c(0,150), type= 'l')
fore.arima.wge(x010[1:100],d= 1,n.ahead= 50)
points(t[101:150],x010[101:150], type= 'l')
```



### Page 301-302
```r
est.ar.wge(x010,p= 1)

t= 1:150
plot(t[1:100],x010[1:100],xlim= c(0,150), type= 'l')
fore.arma.wge(x010[1:100],phi= .965,n.ahead= 50)
points(t[101:150],x010[101:150], type= 'l')

roll.win.rmse.wge(x010,horizon = 50,d = 1) #ARIMA(0,1,0)
roll.win.rmse.wge(x010,horizon = 50, phi = .965) #AR(1)
```



### Page 302-303
```r
x210= gen.arima.wge(n= 250,phi= c(1.3,- .65),d= 1,sn= 4855)
fore.210= fore.arima.wge(x210,phi= c(1.25,- .64),d= 1,n.ahead= 50)

x210= gen.arima.wge(n= 250,phi= c(1.3,- .65),d= 1,sn= 4855,plot= FALSE)
t= 1:250
plot(t[1:200],x210[1:200],xlim= c(0,250),type= 'l',xlab= 'Time')
fore.210= fore.arima.wge(x210[1:200],phi= c(1.25,- .64),d= 1,n.ahead= 50)
fore.210= fore.arima.wge(x210[1:200],phi= c(1.25,- .64),d= 1,n.ahead= 50)
points(t[201:250],x210[201:250],type= 'l')
```


### Page 303-304
```r
par(mfrow= c(2,2))
x220= gen.arima.wge(n= 2000,phi= c(1.3,- .65),d= 2,sn= 450,plot= FALSE)
t= 1:2000
plot(t[1:200],x220[1:200],xlim= c(0,250),type= 'l',xlab= 'Time')
fore.220= fore.arima.wge(x220[1:200],phi= c(1.33,- .69),d= 2,n.ahead= 50)
abline(v= 200)
fore.220= fore.arima.wge(x220[1:200],phi= c(1.33,- .69),d= 2,n.ahead= 50)
points(t[201:250],x220[201:250],type= 'l',lwd= 2,col= 'black')
abline(v= 200)
plot(t,x220, type= 'l')
abline(v= 200)
```



### Page 305-306
```r
xA4= gen.arima.wge(n= 72,s= 4,mu= 50,sn= 52)
xA12= gen.arima.wge(n= 72,s= 12,mu= 50,sn= 100)

plot(xA4[1:24],type= 'l',xlab= 'Time')
abline(v= 4.5,lty= 2);abline(v= 8.5,lty= 2);abline(v= 12.5,lty= 2)
abline(v= 16.5,lty= 2);abline(v= 20.5,lty= 2)
plot(xA12[1:24],type= 'l',xlab= 'Time')
abline(v= 12.5,lty= 2)

factor.wge(phi= c(0,0,0,1))

factor.wge(phi= c(rep(0,3),1))
```


### Page 307
```r
factor.wge(phi= c(0,0,0,0,0,0,0,0,0,0,0,1))
factor.wge(phi= c(rep(0,11),1))
```


### Page 308
```r
xA4= gen.arima.wge(n= 72,s= 4,mu= 50,sn= 52)
xA12= gen.arima.wge(n= 72,s= 12,mu= 50,sn= 100)
plotts.sample.wge(xA4)
plotts.sample.wge(xA12,trunc= 32)
```


### Page 309-310
```r
xB= gen.arima.wge(n= 100,s= 4,phi= c(1.3,- .65),sn= 290)
sB= artrans.wge(xB,phi.tr= c(0,0,0,1),plot= FALSE)
plotts.sample.wge(xB)
plotts.sample.wge(sB)

data(AirPassengers)
logAP= log(AirPassengers)
plotts.sample.wge(logAP)
```


### Page 312-313
```r
est.ar.wge(xA12,p= 16,type= 'burg')

sA12= artrans.wge(xA12,phi.tr= c(rep(0,11),1))
```


### Page 314  Note:  The last two lines are correct here but incorrect in the text.  
```r
Specifically, in each line there should be comma  before arlimits and the addition of ,trunc=30

xA12= gen.arima.wge(n= 72,s= 12,mu= 50,sn= 100)
sA12= artrans.wge(xA12,phi.tr= c(rep(0,11),1),plot= FALSE)
plotts.sample.wge(xA12,arlimits=TRUE,speclimits=c(-20,10),trunc=30)

plotts.sample.wge(sA12 ,arlimits=TRUE,speclimits=c(-20,10),trunc=30)

xB= gen.arima.wge(n= 100,phi= c(1.3,- .65),s= 4,sn= 290)
est.ar.wge(xB, p= 10,type= 'burg')
```

### Page 315
```r
sB4= artrans.wge(xB,phi.tr= c(0,0,0,1))
aic.wge(sB4,p= 0:10,q= 0:2)
est.ar.wge(sB4,p= 2)
```


### Page 316
```r
data(AirPassengers)
logAP= log(AirPassengers)
plotts.sample.wge(logAP)

est.ar.wge(logAP,p= 15,type= 'burg')
```



### Page 317   Note:  The should be a comma before speclimits in each of the last 2 lines
```r
s12= artrans.wge(logAP,phi.tr= c(rep(0,11),1))
s12d1= artrans.wge(s12,phi.tr= 1)

aic5.wge(s12d1,p= 0:15,q= 0:2)

est.ar.wge(s12d1,p= 13,type= 'burg')

data(AirPassengers)
logAP= log(AirPassengers)
s12= artrans.wge(logAP,phi.tr= c(rep(0,11),1),plot= FALSE)
s12d1= artrans.wge(s12,phi.tr= 1,plot= FALSE)
plotts.sample.wge(logAP)
plotts.sample.wge(s12d1,arlimits= TRUE, speclimits=c(-20,10))
plotts.sample.wge(s12,arlimits= TRUE, speclimits=c(-20,10))
```


### Page 319
```r
s12= artrans.wge(airlog,phi.tr= c(rep(0,11),1))
aic5.wge(s12,p= 0:15,q= 0:0)
# AIC selects an AR(13)
est.ar.wge(s12,p= 13)

data(dfw.mon)
DFW.2000= window(dfw.mon,start= c(2000,1))
plotts.sample.wge(DFW.2000)
```


### Page 320-321
```r
DFW.tr12= artrans.wge(DFW.2000,phi.tr= c(1.732,- 1),plot= FALSE)
plotts.sample.wge(DFW.tr12)

aic5.wge(DFW.tr12,p= 0:15,q= 0:2)
```


### Page 322
```r
xA12= gen.arima.wge(n= 72,s= 12,mu= 50,sn= 100)
par(mfrow= c(1,2))
fore.arima.wge(xA4[1:24],s= 4,n.ahead= 12,limits= FALSE)
abline(v= 24.5,lwd= 2)

fore.arima.wge(xA12[1:24],s= 12,n.ahead= 12,limits= FALSE)
abline(v= 24.5,lwd= 2)
```


### Page 323
```r
xB= gen.arima.wge(n= 100,phi= c(1.3,- .65),s= 4,sn= 290)
fore.xB= fore.arima.wge(xB,phi= c(1.19,- .64),s= 4,n.ahead= 12)

xB= gen.arima.wge(n= 112,phi= c(1.3,- .65),s= 4,sn= 290,plot= FALSE)
t= 1:112
plot(t[1:100],xB[1:100],type= 'l',xlim= c(0,120))
fore.xB= fore.arima.wge(xB[89:100],phi= c(1.19,- .64),s= 4,n.ahead= 12)

fore.xB= fore.arima.wge(xB[89:100],phi= c(1.19,- .64),s= 4,n.ahead= 12,limits=
FALSE)
points(t[13:24],xB[101:112],type= 'o')
```

### Page 325
```r
data(AirPassengers)
logAP= log(AirPassengers)
s12= artrans.wge(logAP,phi.tr= c(rep(0,11),1),plot= FALSE)
s12d1= artrans.wge(s12,phi.tr= 1,plot= FALSE)
estAIRLINE = est.ar.wge(s12d1,p= 13,type= 'burg')
roll.win.rmse.wge(logAP, s = 12, d = 1, phi = estAIRLINE$phi, horizon = 12)

aic5.wge(s12,p= 0:15,q= 0:0)
# AIC selects an AR(13)
estALT = est.ar.wge(s12,p= 13)
roll.win.rmse.wge(airlog, s = 12, d = 0, phi = estALT$phi,
horizon = 12)
```



### Page 326
```r
DFW.tr2= artrans.wge(DFW.2000,phi.tr= c(1.732,- 1),plot= FALSE)
est.tr2= est.arma.wge(DFW.tr2,p= 11,q= 1)

seas.12= c(1.732,- 1)
DFW.13= mult.wge(fac1= est.tr2$phi,fac2= seas.12)
```


### Page 327
```r
DFW.full= DFW.13$model.coef
f12= fore.arma.wge(DFW.2000,phi= DFW.13$model.coef,theta= est.tr2$theta,
lastn= TRUE,n.ahead= 12,limits= FALSE)

f36= fore.arma.wge(DFW.2000,phi= DFW.13$model.coef,theta= est.tr2$theta,
lastn= TRUE,n.ahead= 36,limits= FALSE)

f84= fore.arma.wge(DFW.2000,phi= DFW.13$model.coef,theta= est.tr2$theta,
lastn= TRUE,n.ahead= 84,limits= FALSE)

f132= fore.arma.wge(DFW.2000,phi= DFW.13$model.coef,theta= est.tr2$theta,
lastn= TRUE,n.ahead= 132,limits= FALSE)
```



### Page 330
```r
set.seed(11)
par(mfrow= c(4,1), mar=c(2,1,1,1))
u1= gen.arch.wge(500,alpha0= 1,alpha= 0)
u2= gen.arch.wge(500,alpha0= .6,alpha= .4)
u3= gen.arch.wge(500,alpha0= .3,alpha= .7)
u4= gen.arch.wge(500,alpha0= .1,alpha= .9)
```


### Page 334
```r
u1= gen.arch.wge(1000,alpha0= .1,alpha= c(.5,.4),sn= 17)
u2= gen.arch.wge(1000,alpha0= .1,alpha= c(.4,.3,.2),sn= 32)
u3= gen.garch.wge(1000,alpha0= .1,alpha= .4,beta= .5,sn= 141)
```


### Page 335
```r
u1.out= garch(u1,order= c(0,2))
summary(u1.out)
```



### Page 336   Note:  the last line should read summary(u2.out) instead of u2.out in the text
```r
u2.out= garch(u2,order= c(0,3)) # recall, order=c(q,p)
summary(u2.out)
```


### Page 336   
```r
data(rate)
rate.2000= rate[7200:8199]
rate.2000.out= garch(rate.2000,order= c(1,2) # recall, order=c(q,p))
summary(rate.2000.out)
```


### Page 336   Note: Can’t find data set rate 
```r
data(rate)
rate.2000= rate[7200:8199]
rate.2000.out= garch(rate.2000,order= c(1,2) # recall, order=c(q,p))
summary(rate.2000.out)
```


### Page 345
```r
z= gen.arma.wge(n= 100,phi= .95,sn= 447,plot= FALSE)
t= 1:100
line= 10+ .08*t
x= line+ z
plotts.wge(x)   

reg= slr.wge(x)

plotts.wge(x)
fit= reg$b0hat+ t*reg$b1hat
points(fit,type= 'l')

resid= x- fit
plot(resid,type= 'l')
abline(h= 0)
```


### Page 346
```r
z1= gen.arma.wge(n= 100,phi= .90,sn=65987)
time= 1:100
x1= 10+ .1*time+ z1
plotts.wge(x1)

x1= gen.sigplusnoise.wge(n= 100,b0= 10,b1= .1,phi= .9,sn= 65987)

z2= gen.arma.wge(n= 100,phi= .95,sn= 6587)
time= 1:100
x2= 10+ z2
```

### Page 347
```r
slr.wge(x1)
slr.wge(x2)
```


### Page 352
```r
co.wge(x1)
co.wge(x2)
```


### Page 353
```r
wbg.boot.wge(x1)
wbg.boot.wge(x2)
```


### Page 354
```r
wbg.boot.wge(x1,sn= 234)
wbg.boot.wge(x2,sn= 183)
```


### Page 355
```r
xa= slr.wge(x1)

xa$res

xa.aic= aic.burg.wge(xa$res,p= 1:5)
```

### Page 356
```r
x1= gen.sigplusnoise.wge(n= 100,b0= 10,b1= .1,phi= .9,sn= 65987)

wbg.boot.wge(x1)

xa= slr.wge(x1)

xa.aic= aic.wge(xa$res,p= 0:5,q= 0:0)
```



### Page 357-358
```r
fit.sig= fore.sigplusnoise.wge(x1,linear= TRUE)

z2= gen.arma.wge(n= 100,phi= .95,sn= 6587)
x2= 10+ z2

wbg.boot.wge(x2)

aic.wge(x2,p= 0:8,q= 0:2)
```


### Page 359    Note:  Figure 8.4(a) is incorrect.  
```r
xa= slr.wge(x1)

xa.aic= aic.ar.wge(xa$res,p= 0:5)

f.z11= fore.arma.wge(xa$res,xa.aic$phi,n.ahead= 25)

tf= 101:125
f.x1= f.z1$f+ xa$b0hat+ xa$b1hat*tf

fore.sigplusnoise.wge(x1,n.ahead= 25,limits= TRUE)
```


### Page 360
```r
z= gen.arma.wge(n= 100,phi= .75,sn= 921,vara= 1.5)
time= 1:100
sig.cos= 5*cos(2*pi*.1*time+ pi/ 3)
x.cos= sig.cos+ z
plotts.wge(x.cos)
```


### Page 363-364
```r
n= length(x.cos)
h1= rep(0,n)
h2= rep(0,n)
f.est= .1
for(t in 1:n) h1[t] = cos(2*pi*f.est*t)
for(t in 1:n) h2[t] = sin(2*pi*f.est*t)

h.est= lm(x.cos~h1+ h2)

h.est$coefficients[1] # - .0339
h.est$coefficients[2] # 2.7590
h.est$coefficients[3] # - 4.6649

z.cos= rep(0,n)
C0= h.est$coefficients[1]
A= h.est$coefficients[2]
B= h.est$coefficients[3]
for(t in 1:n) z.cos[t] = x.cos[t]- C0- A*h1[t]- B*h2[t]

z.cos.aic= aic.wge(z.cos,p= 1:5)

ar.cos= est.ar.wge(z.cos,p= z.cos.aic$p)
```



### Page 365
```r
f.ar.cos= fore.arma.wge(ar.cos$res,ar.cos$phi,n.ahead= 50)

f.x.cos= rep(0,length(x.cos))
for (t in 1:length(x.cos))
f.x.cos[t] = f.ar.cos$f[t]+ C0+ A*h1[t]+ B*h2[t]
```


### Page 366
```r
fore.sigplusnoise.wge(x.cos,linear= FALSE,freq= .1,n.ahead= 50,limits= TRUE)

fore.sigplusnoise.wge(x.cos,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
10,limits= FALSE)
fore.sigplusnoise.wge(x.cos,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
43,limits= FALSE)
fore.sigplusnoise.wge(x.cos,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
67,limits= FALSE)
fore.sigplusnoise.wge(x.cos,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
84,limits= FALSE)
```


### Page 368   Note:  The # signs need to be added to the last three lines as shown below
```r
x.ar2= gen.arma.wge(n= 100,phi= c(1.55,- .925),vara= .8,sn= 281)

x.ar2.h= fore.sigplusnoise.wge(x.ar2,linear= FALSE, f= .1)

x.ar2.h$b[1]  # 0.0042891 (C0)
x.ar2.h$b[2]  # - 0.4445196 (A)
x.ar2.h$b[3]  # - 3.4193501 (B)
```

### Page 369   
```r
fore.sigplusnoise.wge(x.ar2,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
10,limits= FALSE)
fore.sigplusnoise.wge(x.ar2,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
43,limits= FALSE)
fore.sigplusnoise.wge(x.ar2,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
67,limits= FALSE)
fore.sigplusnoise.wge(x.ar2,linear= FALSE,freq= .1,lastn= TRUE,n.ahead=
84,limits= FALSE)
```

### Page 371   
```r
dfw.2000= window(dfw.mon,start= c(2000,1))

fore.sigplusnoise.wge(dfw.2000,linear= FALSE,f= .0833)
```


### Page 385   
```r
modelB= gen.arma.wge(n= 150,phi= c(2.6,- 3.34,2.46,- .9024),sn= 3233)
plotts.sample.wge(modelB)
aic.B= aic.wge(modelB,p= 0:10,q= 0:4)# AIC selects p= 4,q= 0
fit40= est.arma.wge(modelB,p= 4,q= 0)

plotts.sample.wge(fit40$res,lag.max= 48,arlimits= TRUE)

ljung.wge(fit40$res,p= 4,q= 0) # K= 24 is the default
ljung.wge(fit40$res,p= 4,q= 0,K= 48)
```


### Page 386   
```r
d1= artrans.wge(airlog,phi.tr= 1) # d1 is the differenced data
d1.s12= artrans.wge(d1,phi.tr= c(rep(0,11),1)) #seasonally difference d1
air.est= est.ar.wge(d1.s12,p= 13,type= 'burg')
plotts.sample.wge(air.est$res,lag.max= 48,arlimits= TRUE)
ljung.wge(air.est$res,p= 13)
ljung.wge(air.est$res,p= 13,K= 48)
```



### Page 387   
```r
data(dfw.mon)
dfw.2000= window(dfw.mon,start= c(2000,1))
tr2.temp= artrans.wge(dfw.2000,phi.tr= c(1.732,- 1))
tr2.est= est.arma.wge(tr2.temp,p= 11,q= 1)
plotts.sample.wge(tr2.est$res,lag.max= 48,arlimits= TRUE)
ljung.wge(tr2.est$res,p= 11,q= 1)
ljung.wge(tr2.est$res,p= 11,q= 1,K= 48)
```



### Page 388   Note:  Should be using sunspot2.0 instead of sunspot.new 
```r
data(sunspot2.0)
ss2= est.ar.wge(sunspot2.0,p= 2)
ljung.wge(ss2$res,p= 2)
ljung.wge(ss2$res,p= 2,K= 48)
```


### Page 389   Note:  The ljung.wge  p-values are 0.0678 and 0.0547
```r
data(sunspot2.0)
ss9= est.ar.wge(sunspot2.0,p= 9)
ljung.wge(ss9$res,p= 9)
ljung.wge(ss9$res,p= 9,K= 48)
```



### Page 390     Note:  p-value is .1809
```r
shapiro.test(fit40$res)
```


### Page 392  
```r
data(global2020)
aic.wge(global2020,p= 0:10,q= 0:4) #AIC selects p= 4,q= 1
aic.wge(global2020,p= 0:10,q= 0:4,type= 'bic') #BIC selects p= 3,q= 0
global41.est= est.arma.wge(global2020,p= 4,q= 1)

plotts.sample.wge(global41.est$res,lag.max= 48,arlimits= TRUE)
ljung.wge(global41.est$res,p= 4,q= 1)
ljung.wge(global41.est$res,p= 4,q= 1,K= 48)
shapiro.test(global41.est$res)
```


### Page 394  
```r
fore.41= fore.arma.wge(global2020,phi=c(.9,-.102,.077,.116),theta=.406,
n.ahead= 50,limits= FALSE)
```


### Page 396  
```r
data(global2020)
y= artrans.wge(global2020,phi.tr= 1)
aic.wge(y,p= 0:10,q= 0:4,type= 'bic')
# AIC and AICC select an MA(2)while BIC picks MA(1)
# As discussed, we select an MA(1)
y.est= est.arma.wge(y,p= 0,q= 1)

plotts.sample.wge(y.est$res,arlimits= TRUE)
ljung.wge(y.est$res,p= 0,q= 1)
ljung.wge(y.est$res,p= 0,q= 1,K= 48)
shapiro.test(y.est$res)
```



### Page 400   Note:  in the next to last line of code, wbg.boot.wge should replace wbg.wge
```r
reg= slr.wge(global2020)
t= 1:length(global2020)
# residuals from the linear regression line
zhat= global2020- reg$b0hat- reg$b1hat*t
```



### Page 401
```r
aic.wge(zhat,p= 0:10,q= 0:0)

global.co= co.wge(global2020,maxp= 10)
global.wbg= wbg.boot.wge(global2020)

zhat= est.ar.wge(zhat,p= 4)
```



### Page 402
```r
plotts.sample.wge(zhat$res,lag.max= 48,arlimits= TRUE)
ljung.wge(zhat$res,p= 4)
ljung.wge(zhat$res,p= 4,K= 48)
shapiro.test(zhat$res)
```


### Page 406
```r
data(global2020)
x.hw= HoltWinters(global2020,gamma= FALSE)
x.pred= predict(x.hw,n.ahead= 50)
plot(x.hw,x.pred,lty= 1:2)
```

### Page 407
```r
logss= log(sunspot2.0+ 10)
```


### Page 408
```r
aic.wge(logss,p= 0:12,q= 0:4)

pacf.wge(logss)
```


### Page 409
```r
data(sunspot2.0)
logss= log(sunspot2.0+ 10)
ss2= est.ar.wge(logss,p= 2)
ss9= est.ar.wge(logss,p= 9)

ljung.wge(ss2$res,p= 2)
ljung.wge(ss2$res,p= 2,K= 48)

ljung.wge(ss9$res,p= 9)
ljung.wge(ss9$res,p= 9,K= 48)
```



### Page 419  
```r
par(mfrow= c(2,2))
data(Bsales)
sales= Bsales$sales
ad_tv= Bsales$ad_tv
ad_online= Bsales$ad_online
discount= Bsales$discount
plotts.wge(sales,xlab= "Week",ylab= "Dollars (in thousands)")
plotts.wge(ad_tv,xlab= "Week",ylab= " Dollars (in thousands)")
plotts.wge(ad_online,xlab= "Week",ylab= " Dollars (in thousands)")
plotts.wge(discount,xlab= "Week",ylab= " Dollars (in thousands)")
```

### Page 420  
```r
data(Bsales)
sales=Bsales$sales
ad_tv=Bsales$ad_tv
ad_online=Bsales$ad_online
discount=Bsales$discount
mlrfit = lm(sales~ad_tv+ ad_online+ discount)
#Base R function for multiple linear regression
aic.wge(mlrfit$residuals, p= 0:8, q= 0)
#Selects the optimal p for an AR(p) fit to the residuals- chooses p= 7
#the residuals were stored in mlrfit.
# The following computes the ML estimates
fit = arima(sales,order= c(7,0,0),xreg= cbind(ad_tv,ad_online,discount))
fit
```


### Page 422  
```r
t = 1:100
mlrfit = lm(sales~ t+ ad_tv+ ad_online+ discount,data=Bsales)
aic.wge(mlrfit$residuals, p= 0:8, q= 0)
#AIC selects p= 6 when fitting the residuals remaining after the MLR fit
fit= arima(Bsales$sales, order= c(6,0,0),xreg= cbind(t,ad_tv,ad_online,discount))
fit
```


### Page 423  Note:  there should only be one closing parenthesis (instead of 2) toward the end of line 6 
```r
plotts.sample.wge(fit$resid,arlimits= TRUE)
ljung.wge(fit$resid,p= 6)
ljung.wge(fit$resid,K= 48,p= 6)

ad_tv1= dplyr::lag(Bsales$ad_tv,1)#Creating lag 1 for ad_ tv
ad_online1= dplyr::lag(Bsales$ad_online,1)#Creating lag 1 for ad_online
discount= Bsales$discount #No lag for discount
Bsales$ad_tv1= ad_tv1 #Add lag (k= 1) ad_tv1 to dataset
Bsales$ad_online1= ad_online1 #Add lag (k= 1) ad_online1 to dataset
mlrfit= lm(sales~ad_tv1+ ad_online1+ discount,data=Bsales)#least sqr regression
aic.wge(mlrfit$residuals,p= 0:8,q= 0) #AIC selects p= 7 fit to residuals
fit= arima(Bsales$sales,order= c(7,0,0), xreg= cbind(ad_tv1,ad_online1,discount))
fit
```

### Page 424  
```r
plotts.sample.wge(fit$resid[2:100],lag.max= 50,arlimits= TRUE)
ljung.wge(fit$resid[2:100],p= 7)
ljung.wge(fit$resid[2:100],p= 7,K= 48)
```


### Page 425  
```r
t= 1:100 #Adding 100 trend weeks. Remaining code is similar to previous example.
ad_tv1= dplyr::lag(ad_tv,1)
ad_online1= dplyr::lag(ad_online,1)
mlrfit= lm(sales ~ t+ ad_tv1+ ad_online1+ discount)
aic.wge(mlrfit$residuals,p= 0:8,q= 0) #AIC selects p= 7
fit= arima(sales,order= c(7,0,0),xreg= cbind(t,ad_tv1,ad_online1,discount))
fit

plotts.sample.wge(fit$resid[2:100],lag.max= 50,arlimits= TRUE)
ljung.wge(fit$resid[2:100],p= 7)
ljung.wge(fit$resid[2:100],p= 7,K= 48)
```

### Page 427  
```r
ccf(ad_tv,sales) #Figure 10.6(a)7
ccf(ad_online,sales) #Figure 10.6(b)
ccf(discount,sales) #Figure 10.6(c)
```

### Page 430  
```r
x1.25= c( - 1.03, 0.11, - 0.18, 0.20, - 0.99, - 1.63, 1.07, 2.26, - 0.49, - 1.54, 0.45,
0.92, - 0.05, - 1.18, 0.90, 1.17, 0.31, 1.19, 0.27, - 0.09, 0.23, - 1.91, 0.46,
3.61, - 0.03)
x2.25= c( - 0.82, 0.54, 1.13, - 0.24, - 0.77, 0.22, 0.46, - 0.03, - 0.59, 0.45, 0.59,
0.15, 0.60, 0.13, - 0.04, 0.12, - 0.96, 0.23, 1.81, - 0.01, - 0.95, - 0.55, - 0.15,
0.71, 0.90)

ccf(x1.25,x2.25) ## cross- correlation shows the significant lag at 5 ##
```



### Page 431  
```r
x1= x1.25[1:20]
x2= x2.25[1:20]

p1= aic.wge(x1,p= 0:8,q= 0:0) # aic picks p= 2
x1.est= est.ar.wge(x1,p= p1$p)
fore.arma.wge(x1.25,phi= x1.est$phi,n.ahead= 5,lastn= TRUE,limits= FALSE)
#
p2= aic.wge(x2,p= 0:8,q= 0:0) # aic picks p= 2
x2.est= est.ar.wge(x1,p= p2$p)
fore.arma.wge(x2.25,phi= x2.est$phi,n.ahead= 5,lastn= TRUE,limits= FALSE)
#
```


### Page 432    Results don’t match output in book
```r
# You will need to install and load the vars package from CRAN
library(vars)
X= cbind(x1,x2)
VARselect(X,lag.max= 6,type= "const",season= NULL,exogen= NULL)
# AIC and BIC(SC) select p= 5

lsfit= VAR(X,p= 5,type= "const")
summary(lsfit) ##Note significance of 1 variable, at lag 5 ##
```

### Page 433    Note:  The last line of code has been changed from the version in the text
```r
# VAR forecasting
preds= predict(lsfit,n.ahead= 5)

f1.12= preds$fcst$x1[,1] # VAR forecasts for x1
f2.12= preds$fcst$x2[,1] # VAR forecasts for x2
# Plotting Forecasts of x1.25
t= 1:25
plot(t,x1.25,type= "o",pch= 20,cex= 1,ylim= c(-2,3.75))
points(t[20:25],c(x1[20],f1.12),type= 'o',cex= 2,pch= 1)
# Plotting Forecasts of x2.25
plot(t,x2.25,type= "o",pch= 20,cex= 1,ylim= c(-2,3.75))
points(t[20:25],c(x2[20],f2.12),type= 'o',cex= 2,pch= 1)
```


### Page 434    
```r
melanoma= c(1.0,0.9,0.8,1.4,1.2,1.0,1.5,1.9,1.5,1.5,1.5,1.6,1.8,2.8,2.5,2.5,
2.4,2.1,1.9,2.4,2.4,2.6,2.6,4.4,4.2,3.8,3.4,3.6,4.1,3.7,4.2,4.1,4.1,4.0,5.2,
5.3, 5.3)
sunspot= c(133,191,183,148,113,79,51,27,16,55,154,215,193,191,119,98,45,20,7,
54,201,269,262,225,159,76,53,40,15,22,67,133,150,149,148,94,98)
t= 1:37
year= 1935+ t
plot(year,sunspot,type= 'o',pch= 20)
plot(year,melanoma,type= 'o',pch= 20)
ccf(sunspot,melanoma,ylim= c(- 1,1))

mel.64= melanoma[1:29]
sun.64= sunspot[1:29]
```

### Page 435    
```r
## Univariate analysis/ forecasts for melanoma ##
p.mel= aic.wge(mel.64,p= 0:10,q= 0:0)
p.mel$p
mel.est= est.ar.wge(mel.64,p= p.mel$p)
pred_m= fore.arma.wge(mel.64,phi= mel.est$phi,n.ahead= 8,lastn= FALSE,limits=
FALSE)
plot(year,melanoma,type= 'o',pch= 20)
points(year[29:37],c(melanoma[29],pred_m$f),type= 'o',lty= 2,pch= 1)
## Univariate analysis/ forecasts for sunspot ##
p.sun= aic.wge(sun.64,p= 0:10,q= 0:0)
p.sun$p
sun.est= est.ar.wge(sun.64,p= p.sun$p)
pred_s= fore.arma.wge(sun.64,phi= sun.est$phi,n.ahead= 8,lastn= FALSE,limits=
FALSE)
plot(year,sunspot,type= 'o',pch= 20)
points(year[29:37],c(sunspot[29],pred_s$f),type= 'o',lty= 2,pch= 1)

X= cbind(mel.64,sun.64)
VARselect(X, lag.max = 5, type = "const",season = NULL, exogen = NULL)
#AIC = 5, BIC picks 4. We go with 4.

VARfit= VAR(X,p= 4,type= 'const') ## This fits 9 parameters ##
```


### Page 436  Note: The actual sunspot values are incorrectly plotted in Figure 10.12(b)
```r
preds= predict(VARfit,n.ahead= 8)
mel.f= preds$fcst$mel.64[,1] # VAR forecasts for mel.64
sun.f= preds$fcst$sun.64[,1] # VAR forecasts for sun.64

t= 1:37
year= t+ 1935
# melanoma forecasts
plot(year,melanoma,type= "o",pch= 20,cex= 1,ylim= c(.5,6))
points(year[29:37],c(melanoma[29],mel.f),type= 'o',cex= 1,pch= 1)
# sunspot forecasts
plot(year,sunspot,type= "o",pch= 20,cex= 1)
points(year[29:37],c(sunspot[29],sun.f),type= 'o',cex= 1,pch= 1)

RMSE_AR= sqrt(mean((melanoma[30:37]- pred_m$f[1:8])^2))
RMSE_VAR= sqrt(mean((melanoma[30:37]- preds$fcst$mel.64[1:8])^2))
```

### Page 437  
```r
data(cardiac)
head(cardiac)
```


### Page 439  
```r
VARselect(cardiac, lag.max = 10, type = "both")
```



### Page 440   
```r
cardiacTrain = window(cardiac, start = c(1970,1), end = c(1978,40))
cardiacTest = window(cardiac, start = c(1978,41), end = c(1979,40))

CMortVAR2 = VAR(cardiacTrain, type = "both", p = 2)
CMortVAR9 = VAR(cardiacTrain, type = "both", p = 9)
CMortVAR7 = VAR(cardiacTrain, type = "both", p = 7)

ljung.wge(CMortVAR2$varresult$cmort$residuals,p= 2)
ljung.wge(CMortVAR9$varresult$cmort$residuals,p= 9)
ljung.wge(CMortVAR7$varresult$cmort$residuals,p= 7)

preds2= predict(CMortVAR2,n.ahead= 52)
preds9= predict(CMortVAR9,n.ahead= 52)
preds7= predict(CMortVAR7,n.ahead= 52)

t= 1:508
plot(t, cardiac[,"cmort"], type = "l", xlim = c(450,510), ylab = "Cardiac
Mortality", main = "52 Week Cardiac Mortality Forecast", xlab = "Time")
points(t[457:508], preds2$fcst$cmort[,1], type= "l", lwd= 2, lty= 1)
points(t[457:508], preds9$fcst$cmort[,1], type= "l", lwd= 2, lty= 2)
points(seq(457,508,1), preds7$fcst$cmort[,1], type= "l", lwd= 2,lty= 3)
RMSE2 = sqrt(mean((cardiacTest[,"cmort"] - preds2$fcst$cmort[,1])^2))
RMSE9 = sqrt(mean((cardiacTest[,"cmort"] - preds9$fcst$cmort[,1])^2))
RMSE7 = sqrt(mean((cardiacTest[,"cmort"] - preds7$fcst$cmort[,1])^2))
```


### Page 442   Note: In last 3 lines t[457,508] in text has been changed to t[457:508] 
```r
VARselect(cardiac, lag.max = 10, season = 52, type = "both")

CMortVAR2 = VAR(cardiacTrain, type = "both", season = 52, p = 2)
CMortVAR9 = VAR(cardiacTrain, type = "both", season = 52, p = 9)
CMortVAR7 = VAR(cardiacTrain, type = "both", season = 52, p = 7)

ljung.wge(CMortVAR2$varresult$cmort$residuals,p= 2)
ljung.wge(CMortVAR9$varresult$cmort$residuals,p= 9)
ljung.wge(CMortVAR7$varresult$cmort$residuals,p= 7)

preds2= predict(CMortVAR2,n.ahead= 52)
preds9= predict(CMortVAR9,n.ahead= 52)
preds7= predict(CMortVAR7,n.ahead= 52)

plot(seq(1,508,1), cardiac[,"cmort"], type = "l", xlim = c(450,510), ylab =
"Cardiac Mortality", main = "52 Week Cardiac Mortality Forecast", xlab =
"Time")
t= 1:508
points(t[457:508], preds2$fcst$cmort[,1], type= "l", lwd= 2, col = "red")
points(t[457:508], preds9$fcst$cmort[,1], type= "l", lwd= 2, col = "blue")
points(t[457:508], preds7$fcst$cmort[,1], type= "l", lwd= 2, col = "green")
```


### Page 443
```r 
RMSE2 = sqrt(mean((cardiacTest[,"cmort"] - preds2$fcst$cmort[,1])^2))
RMSE9 = sqrt(mean((cardiacTest[,"cmort"] - preds9$fcst$cmort[,1])^2))
RMSE7 = sqrt(mean((cardiacTest[,"cmort"] - preds7$fcst$cmort[,1])^2))
```


### Page 444
```r
CMortVAR7 = VAR(cardiac, type = "both", p = 7)
preds7= predict(CMortVAR7,n.ahead= 52)
#cmort forecasts
head(preds7$fcst$cmort) #cardiac mortality forecasts
head(preds7$fcst$temp) # temperature forecasts
head(preds7$fcst$part) # particulates forecasts

plot(seq(1,508,1), cardiac[,"cmort"], type = "l",xlim = c(450,560), ylim =
c(50,112),xlab = "Time", ylab = "Cardiac Mortality", main = "52 Week Cardiac
Mortality Forecast From a VAR with p = 7")

t= 1:560
points(t[509:560],preds7$fcst$cmort[,2], type = "l", lwd = 1, lty = 3)
points(t[509:560],preds7$fcst$cmort[,1] , type = "l", lwd = 1.5, lty = 1)
points(t[509:560],preds7$fcst$cmort[,3] , type = "l", lwd = 1, lty = 3)
```


### Page 459
```r
set.seed(1) 
AR1Fit = mlp(wtcrude2020, m = 1, hd = 0, lags = 1, difforder = 0, reps = 5)
plot(AR1Fit)

AR1Fit

AR1Fit$net$weights
```


### Page 460
```r
estAR1 = est.ar.wge(wtcrude2020,p = 1, type = "burg")
estAR1$phi

preds = forecast(AR1Fit,h = 1)
preds$all.mean

preds$mean # even though this is the median
```




### Page 461
```r
preds = forecast(AR1Fit,h = 10)
preds$all.mean

preds$mean #even though this is still the median
```



### Page 463   
```r
rwAR1Fit = roll.win.rmse.nn.wge(wtcrude2020,horizon = 1,fit_model = AR1Fit)
```


### Page 464   
```r
rwAR1Fit = roll.win.rmse.nn.wge(wtcrude2020,horizon = 10,fit_model = AR1Fit)
```



### Page 465   
```r
set.seed(1) 
AR3Fit = mlp(ts(wtcrude2020),hd = 0, lags = c(1,2,3), difforder = 0,
reps = 5, sel.lag = FALSE)
AR3Fit
```


### Page 466   
```r
set.seed(1) 
AutoFit = mlp(ts(wtcrude2020),hd = 0, lags = c(1,2,3), difforder = 0,
reps = 5, sel.lag = TRUE)
AutoFit
plot(AutoFit)

preds = forecast(AR3Fit,h = 10)
preds$mean

preds = forecast(AutoFit,h = 10)
preds$mean
```



### Page 467   
```r
rwAR3Fit = roll.win.rmse.nn.wge(wtcrude2020,horizon = 10, fit_model = AR3Fit)

rwAutoFit = roll.win.rmse.nn.wge(wtcrude2020,horizon = 10,fit_model= AutoFit)
```


### Page 469   
```r
set.seed(1) 
DeepFit = mlp(ts(wtcrude2020),hd = 2, lags = c(1,2,3), difforder = 0,
reps = 5, sel.lag = FALSE)
DeepFit
plot(DeepFit)
```


### Page 470   
```r
preds = forecast(DeepFit,h = 10)
round(preds$mean, 2)

rwDeepFit = roll.win.rmse.nn.wge(wtcrude2020,horizon = 10,fit_model= DeepFit)
```



### Page 471   
```r
set.seed(1) 
fit.1.12.H5 = mlp(AirPassengers,difforder = c(1,12),allow.det.season = FALSE)
fit.1.12.H5
```


### Page 472   
```r
plot(fit.1.12.H5)

rwfit1.12.H5 = roll.win.rmse.nn.wge(AirPassengers,horizon = 36, fit.1.12.H5)

set.seed(1) 
fit.1.H5 = mlp(AirPassengers,allow.det.season = FALSE)
fit.1.H5
```


### Page 473   
```r
rwfit.1.H5 = roll.win.rmse.nn.wge(AirPassengers,horizon = 36, fit.1.H5)
frequency(AirPassengers)

set.seed(1) 
fitSeasonal = mlp(AirPassengers,allow.det.season = TRUE)
# same as fitSeasonal = mlp(AirPassengers)
fitSeasonal

plot(fitSeasonal)
```


### Page 474   
```r
rwfitSeasonal = roll.win.rmse.nn.wge(AirPassengers,h = 36, fit_model = fitSeasonal)

set.seed(1) 
t = 1:180
fitSeasonal = mlp(AirPassengers,allow.det.season = TRUE)
finalFit = forecast(fitSeasonal, h = 36)
plot(t[1:144], AirPassengers, type = "l", xli = c(0,185), ylim = c(100, 800),
xlab = "Time")
lines(t[145:180], finalFit$mean,lty = 3, lwd = 3)

SMtrain = melanoma2.0[1:29,]
SMtest = melanoma2.0[30:37,]
SMtrainDF = data.frame(Sunspot = ts(SMtrain$sunspot))

set.seed(1) 
fit.mlp1 = mlp(ts(SMtrain$melanoma), lags = 1,reps = 20,comb = "median",
xreg = SMtrainDF, xreg.lags = 1, allow.det.season = FALSE, hd = 3, difforder = 0,
sel.lag = FALSE)
fit.mlp1
plot(fit.mlp1)

set.seed(1) 
fit.mlp.SP = mlp(ts(SMtrainDF$Sunspot),reps = 20, comb = "median")
fore.mlp.SP = forecast(fit.mlp.SP, h = 8)
fore.mlp.SP
```




### Page 477   
```r
plot(fore.mlp.SP)

SMDF_fore = data.frame(Sunspot = ts(fore.mlp.SP$mean))
SMDF = data.frame(Sunspot = ts(c(SMtrainDF$Sunspot,SMDF_fore$Sunspot)))
```


### Page 478   
```r
fore.mlp = forecast(fit.mlp1, h = 8, xreg = SMDF)
fore.mlp

plot(fore.mlp)

RMSE = sqrt(mean((SMtest$melanoma - fore.mlp$mean)^2))
RMSE
```


### Page 479   
```r
set.seed(1) 
fit.mlp2 = mlp(ts(SMtrain$melanoma), reps = 20,comb = "median",
xreg = SMtrainDF, allow.det.season = FALSE)
fit.mlp2
plot(fit.mlp2)

fore.mlp = forecast(fit.mlp2, h = 8, xreg = SMDF)
fore.mlp
plot(fore.mlp)
```


### Page 480   
```r
RMSE = sqrt(mean((SMtest$melanoma - fore.mlp$mean)^2))
RMSE

#refit model using all the data
set.seed(1) 
fit.mlp3 = mlp(ts(melanoma2.0$melanoma), reps = 20,comb = "median",
xreg = data.frame(Sunspot = melanoma2.0$sunspot), allow.det.season = FALSE)
fit.mlp3
```



### Page 481   
```r
set.seed(1) 
fit.mlp.SP = mlp(ts(melanoma2.0$sunspot),reps = 50, comb = "median")
fore.mlp.SP = forecast(fit.mlp.SP, h = 8)
#put the sunpsots in a data frame so they can be input in mlp()
SMDF_fore = data.frame(Sunspot = ts(fore.mlp.SP$mean))
SMDF = data.frame(Sunspot = ts(c(melanoma2.0$sunspot,SMDF_fore$Sunspot)))
#calculate and visualize the forecasts
fore.mlp = forecast(fit.mlp3, h = 8, xreg = SMDF)
fore.mlp

plot(fore.mlp)
```


### Page 483   
```r
cardiacTrain = window(cardiac, start = c(1970,1), end = c(1978,40))
cardiacTest = window(cardiac, start = c(1978,41), end = c(1979,40))

# Temperature
set.seed(1) 
fit.mlp.temp = mlp(ts(cardiacTrain[,"tempr"],frequency = 52),reps = 50, difforder = 0, comb = "median", allow.det.season = TRUE, det.type = "bin")
fit.mlp.temp
plot(fit.mlp.temp)
fore.mlp.temp = forecast(fit.mlp.temp, h = 52)
plot(fore.mlp.temp)
```


### Page 484   
```r
# Particulates
set.seed(1) 
fit.mlp.part = mlp(ts(cardiacTrain[,"part"],frequency = 52),reps = 50, difforder = 0, comb = "median", allow.det.season = TRUE, det.type = "bin")
fit.mlp.part
plot(fit.mlp.part)
fore.mlp.part = forecast(fit.mlp.part, h = 52)
plot(fore.mlp.part)
```



### Page 485
```r
cardiacDF_xreg = data.frame(temp = ts(cardiacTrain[,"tempr"]),
part = ts(c(cardiacTrain[,"part"])))

set.seed(1) 
fit.mlp.cmort = mlp(ts(cardiacTrain[,"cmort"], frequency = 52),reps = 50,comb = "median",xreg = cardiacDF_xreg, allow.det.season = FALSE)
fit.mlp.cmort

plot(fit.mlp.cmort)

CMDF_fore = data.frame(temp = ts(c(cardiacTrain[,"tempr"],fore.mlp.temp$mean)),
part = ts(c(cardiacTrain[,"part"],fore.mlp.part$mean)))

fore.mlp.cmort = forecast(fit.mlp.cmort, h = 52, xreg = CMDF_fore)
plot(fore.mlp.cmort)
RMSE = sqrt(mean((cardiacTest[,"cmort"][1:52] - fore.mlp.cmort$mean)^2))
RMSE
```


### Page 486
```r
cardiacDF_xreg = data.frame(temp = ts(cardiacTrain[,"tempr"]), part =
ts(c(cardiacTrain[,"part"])))
fit.mlp.cmortS = mlp(ts(cardiacTrain[,"cmort"],frequency = 52),reps = 50,comb = "median",xreg = cardiacDF_xreg, allow.det.season = TRUE, det.type = "bin")
fit.mlp.cmortS
plot(fit.mlp.cmortS)

CMDF_fore = data.frame(temp =
ts(c(cardiacTrain[,"tempr"],fore.mlp.temp$mean)), part =
ts(c(cardiacTrain[,"part"],fore.mlp.part$mean)))
```


### Page 487  Note:  RMSE value differs siightly from text
```r
fore.mlp.cmortS = forecast(fit.mlp.cmortS, h = 52, xreg = CMDF_fore)
plot(fore.mlp.cmortS)
RMSE = sqrt(mean((cardiacTest[,"cmort"][1:52] - fore.mlp.cmortS$mean)^2))
RMSE

CMortVAR2S = VAR(cardiacTrain, season = 52, type = "both", p = 2)
preds2S= predict(CMortVAR2S,n.ahead= 52)
```


### Page 488
```r
ensemble = (preds2S$fcst$cmort[,1] + fore.mlp.cmortS$mean)/ 2

#Plot
plot(seq(1,508,1), cardiac[,"cmort"], type = "l",xlim = c(450,508), xlab =
"Time", ylab = "Cardiac Mortality", main = "52 Week Cardiac Mortality Forecast
From A VAR/ MLP Ensemble")
lines(seq(457,508,1), ensemble, type = "l", lwd = 4, col = "green")
RMSEENSEMBLE = sqrt(mean((cardiacTest[,"cmort"] - ensemble)^2))
RMSEENSEMBLE
```
