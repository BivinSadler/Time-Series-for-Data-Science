# Errata  


### Errata in the textbook will be logged here:


Errata Sheet

Page 9   Figure 1.8 (c) and (f) are incorrect.  The corrected Figure 1.8 and caption are given below.

<img src="https://github.com/BivinSadler/Time-Series-for-Data-Science/blob/main/Errata/Figure1_8.jpg" height="500" class="center" >

Page 31    In all of the code, bitcoin should not be capitalized.

Page 43  Note:  Code is modified slightly to give plots(a)-(c)
```r
par(mfrow=c(1,3))
data(tesla)
tesla.3= ma.smooth.wge(tesla,order= 3,plot= FALSE)
tesla.8= ma.smooth.wge(tesla,order= 8,plot= FALSE)
plotts.wge(tesla)
plotts.wge(tesla.3$smooth)
plotts.wge(tesla.8$smooth)
# the plots based on the tswge ts object dfw.yr are obtained analogously
```

Page 44   Note:  This code produces all 6 plots
```r
par(mfrow=c(2,3))
set.seed(6946)
t= 1:60
cosine= cos(2*pi*t/ 10)
line= - 2+ .05*t
w=cosine+line
z= rnorm(n= 60,sd= 1)
x= cosine+ line+ z
plotts.wge(cosine)
plotts.wge(line)
plotts.wge(w)
plotts.wge(z)
plotts.wge(x)
ma.smooth.wge(x,order= 5)
```

Page 48     This code replaces the incorrect code on Page 48
```r
data(tx.unemp.unadj)
tx.unemp.sm= ma.smooth.wge(tx.unemp.unadj,order= 12, plot= FALSE)
tx.unemp.sm12= ts(tx.unemp.sm$smooth,start= c(2000,1),frequency= 12)
plotts.wge(tx.unemp.sm12)
```

Page 65: exp.smooth.wge() is now expsmooth.wge() throughout.  The name had to change due to an R issue with inheriting from S3 exp function.

Page 66  Note:  The third line is added to produce the plot in the text and exp.smooth.wge changed to expsmooth.wge (inheritance issue)
```r
data(dfw.yr)
expsmooth.wge(dfw.yr,alpha= .2,n.ahead= 10)
ma.pred.wge(dfw.yr,n.ahead=10)
```
Page 72  Problem 4:  There should be no caps in  us.retail 

Page 54    This code replaces the incorrect code on page 54
```r
data(tx.unemp.unadj)
tx.unemp.sm= ma.smooth.wge(tx.unemp.unadj,order= 12,plot= FALSE)
tx.unemp.sm12= ts(tx.unemp.sm$smooth,start= c(2000,1), frequency= 12)
plotts.wge(tx.unemp.sm12)
```

Page 62   The last line of code uses n.ahead (which is correct) and not k.ahead
```r
ma5= ma.pred.wge(wtc36,order= 5,n.ahead= 4)
```

Page 103  Table 3.8 should be as shown below.  
Table 3.8: 19 Pairs of Observations in Time Series 2 that Differ by One Time Unit   
t	x_t	x_(t+1)		t	x_t	x_(t+1)  
1	22	13		11	20	27  
2	 13	19		12	27	41  
3	19	22		13	41	44  
4	22	23		14	44	39  
5	23	21		15	39	41  
6	21	15		16	41	56  
7	15	19		17	56	57  
8	19	32		18	57	60  
9	32	20		19	60	61  
10	20	20				  


Page 143    The last line of the code should be 
```r
parzen.wge(high$x.filt)
```
instead of 
```r
parzenww.wge(high$x.filt)
```
which is in the text

Page 204     The second instance of 
```r
plotts.sample.wge  
```
has the .wge left off in the text
```r
plotts.sample.wge
```
(fig5.26d) #this plots Figure 5.26(d- f)

Page 207     The second instance of plotts.sample.wge has the .wge left off in the text

Page 236   In the text the generate statement is missing the theta=.92 part of the generated model
arma31.500= gen.arma.wge(n= 500,phi= c(2.57,- 2.50,.92),theta= .92,mu= 30,sn= 65)

Page 241   aic.ar.wge should not have the q=0:4 parameters in the call statement.
  
Page 269    The parameter specifying the ϕ_j  coefficients is phi,  not phis as is in the text. 
plotts.sample.wge(A_real) # plots(d- f)

Page 282  In plotts.sample.wge on the last line there should be a comma after d1

Page 290  (2)(i) mentions realization lengths of 100,200,500,4000 when it should be 100,200,500,10000.  

Page 292-294   The correct fitted ARIMA(2,1,0) model is (1-1.37B+.73B^2)(1-B)X_t=a_t,    where σ ̂_a^2=1.036.

Page 294   The plotts.sample.wge code in the text has an extra arlimits=TRUE

Page 297   The last two lines should have d2.pop in place of d2

Page 301   For the model in (7.7) and discussion following, xbar=25.56

Page 314  In each of the last two lines of code there should be comma  before arlimits and the addition of ,trunc=30.  Specifically, the correct code is 
```r
plotts.sample.wge(xA12,arlimits=TRUE,speclimits=c(-20,10),trunc=30)
plotts.sample.wge(sA12,arlimits=TRUE,speclimits=c(-20,10),trunc=30)
```
Page 317  The should be a comma before speclimits in each of the last 2 lines

Page 325  In the below segment of code, "type" in the est.ar.wge function is now "method"
```r
data(AirPassengers)
logAP=log(AirPassengers)
s12=artrans.wge(logAP,phi.tr=c(rep(0,11),1),plot=FALSE)
s12d1=artrans.wge(s12,phi.tr=1,plot=FALSE)
estAIRLINE = est.ar.wge(s12d1,p=13,method='burg')
roll.win.rmse.wge(logAP, s = 12, d = 1, phi = estAIRLINE$phi, horizon = 12)
```

Page 335:  The results in the text do not match the results obtained by running the code.  However, conclusions are the same.

Page 336     The last line should read summary(u2.out) instead of u2.out as in the text.  Also, the Box-Ljung results for the u3 output in the text do not match those obtained by running the code.

Page 359      Figure 8.4(a) is incorrect.  The correct figure is shown below.
 
Page 388     The file should be sunspot2.0 instead of sunspot.new 

Page 389     The ljung.wge p-values for ss9$res should be 0.0678 and 0.0547

Page 390  The shapiro.test  p-values should be as follows:
fit40 residuals: .1809
dfw.2000 temperature residuals:  .9598
Sunspot residuals:  7.065e-07

Page 401    wbg.boot.wge should replace wbg.wge

Page 423  There should only be one closing parenthesis (instead of 2) toward the end of line 6 
```r
mlrfit= lm(sales~ad_tv1 + ad_online1+ discount,data=Bsales)#least sqr regression
```

Page 429  Forecast equation at the bottom of the page:  the ϕ_j should be ϕ ̂_j in all cases

Page 430  In the two forecast equations toward the top of the page:   ϕ_ij should be ϕ ̂_ij in all cases

Page 432    Results don’t match output in book

Page 433    The last line of code should be changed to
```r
points(t[20:25],c(x2[20],f2.12),type= 'o',cex= 2,pch= 1)
```

Page 436    The actual sunspot values are incorrectly plotted in Figure 10.12(b). The correct plot is shown below.


Page 442    In the last 3 lines t[457,508] should be changed to t[457:508] 

Page 459    Code should be on separate lines  
```r
set.seed(1)   
AR1Fit = mlp(wtcrude2020, m = 1, hd = 0, lags = 1, difforder = 0, reps = 5)  
```

Page 460    "type" should be "method" and code should be on two separate lines  
```r
estAR1 = est.ar.wge(wtcrude2020,p = 1, method = "burg")  
estAR1$phi  
```

Page 481  The following results which differ slightly from the values in the text and the plot is different as shown below.
   
   Point Forecast  
38       5.202662  
39       5.104457  
40       5.527732  
41       5.263305  
42       5.560360  
43       5.701788  
44       5.748933  
45       5.931066  

                                                      



Page 483     The line in red should be added to the code.
```r
#Temperature  
set.seed(1) 
fit.mlp.temp = mlp(ts(cardiacTrain[,"tempr"],frequency = 52),reps =
50, difforder = 0, comb = "median", allow.det.season = TRUE, det.type = "bin")
fit.mlp.temp
plot(fit.mlp.temp)
fore.mlp.temp = forecast(fit.mlp.temp, h = 52)
plot(fore.mlp.temp)
```




Page 487  RMSE=6.203129  


Page 488   Difficulty caclulating RMSEENSEMBLE ... just need as.numeric around *ensemble*
```r
ensemble = (preds2S$fcst$cmort[,1] + fore.mlp.cmortS$mean)/ 2
#Plot
plot(seq(1,508,1), cardiac[,"cmort"], type = "l",xlim = c(450,508), xlab =
"Time", ylab = "Cardiac Mortality", main = "52 Week Cardiac Mortality Forecast
From A VAR/ MLP Ensemble")
lines(seq(457,508,1), ensemble, type = "l", lwd = 4, col = "green")
RMSEENSEMBLE = sqrt(mean((cardiacTest[,"cmort"] - as.numeric(ensemble))^2))
RMSEENSEMBLE
```
Page 488

The RMSEENSEMBLE should be 5.611912

Page 489 The VAR forecasts are a solid line and should be dashed / dotted


























