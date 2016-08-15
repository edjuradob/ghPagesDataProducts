---
title: "Car classification"
author: "Edgar Jurado"
highlighter: highlight.js
output: pdf_document
job: Classification for buying a car
knit: slidify::knit2slides
mode: selfcontained
hitheme: tomorrow
subtitle: classification recommendation for buying a car
framework: io2012
widgets: []
---

## Application

Taking the dataset in https://archive.ics.uci.edu/ml/datasets/Car+Evaluation
we take the data from https://archive.ics.uci.edu/ml/machine-learning-databases/car/car.data, we get the information and generate a predictive model.

The data is as follows:

1. CAR car acceptability 
2. PRICE overall price 
3. . buying buying price 
4. . maint price of the maintenance 
5. TECH technical characteristics 
6. . COMFORT comfort 
7. . . doors number of doors 
8. . . persons capacity in terms of persons to carry 
9. . . lug_boot the size of luggage boot 
10. . safety estimated safety of the car 


---

## Classifications

The classifications are: 

1. unacceptable - unacc
2. acceptable - acc
3. good - good
4. very good - vgood


--- 


## Parameters

In the application you will get some selects with the options to be filled, they are shown below:

1. buying: vhigh, high, med, low. 
2. maint: vhigh, high, med, low. 
3. doors: 2, 3, 4, 5more. 
4. persons: 2, 4, more. 
5. lug_boot: small, med, big. 
6. safety: low, med, high. 

----

## Prediction methods

We get the predictions with the GBM Algorithm, with an, accuracy of 0.9766764 for recommend the buying of a car. We tried several other algorithms, as the nearest neighborn, random forests, naive bayes, etc, but the GBM was the most accurate.

As we already have the model, we only load the file containing the results to avoid a slow load of this presentation. Then, for an example, we do a dummy test to get the prediction (remember we got an accuracy of 0.9766764 given by the confusionMatrix with 20% of test data)

```r
  load(file="modelGBM.rda")
```

```
## Warning in readChar(con, 5L, useBytes = TRUE): cannot open compressed file
## 'modelGBM.rda', probable reason 'No such file or directory'
```

```
## Error in readChar(con, 5L, useBytes = TRUE): no se puede abrir la conexi�n
```

```r
newData<-data.frame(c("high"), c("med"),c("4"),c("4"),c("med"),c("high"))
names(newData)<-c("buying", "maint","doors","persons","lug_boot","safety")
pGBM<-predict(modelGBM,newdata=newData)
```

```
## Error in predict(modelGBM, newdata = newData): objeto 'modelGBM' no encontrado
```
So we get the following result:

```
## Error in eval(expr, envir, enclos): objeto 'pGBM' no encontrado
```

-----

## Test application and code

You can test the application in https://edjuradob.shinyapps.io/09_dataProducts/

The code is in https://github.com/edjuradob/DataPRoducts
In the folder w3 is the file project.R where I made all the tests for the model


