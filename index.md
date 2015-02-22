---
title       : ShinyClusters
subtitle    : An App for Cluster Identification
author      : CP Montoya
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, quiz, bootstrap]           # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What is ShinyClusters?

* ShinyClusters is an app to identify clusters in two dimensional data

* The app is implemented on the web using Shiny from RStudio

* ShinyClusters uses the k-means algorithm available in r to identify the clusters

* ShinyCluster currently is limited to analyses of the iris data included in r

* The user can choose which two sets of data to use and how many clusters to identify

* The k-means algorithm randomly chooses 25 different starting centers and then finds the best answer

--- .class #id 

## How does ShinyClusters do?

* The iris data contains actual species assignments

* Clicking the actual checkbox will change the cluster assignments to the actual species

---

## How could one decide how many clusters to choose?

* By running the algorithm for a range of clusters and comparing the withinss parameter in the plot below


```r
library(ggplot2)
pdata<-iris['Petal.Length','Sepal.Width']
qplot(c(1:10),sapply(c(1:10),function(x) kmeans(pdata,center=x,nstart=10)$tot.withinss),geom="point",xlab="Number of Clusters",ylab="Total deviations within clusters",main= "Choosing the number of Clusters",size=I(6))+geom_line(size=2)
```

```
## Error: NA/NaN/Inf in foreign function call (arg 1)
```

* The elbow of the graph indcates diminishing returns from adding clusters and so my be the best choice

---

## What impovements could be made?

* Perhaps use different starts to compute average cluster id (soft clusters rather than hard)

