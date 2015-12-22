---
layout: post
title: VLFeat教程之k-means
date: 2015-12-22
categories: MLCV
tags: [VLFeat,k-means]
description: Machine Learning相关

---




This tutorial shows how to use the [K-means algorithm](http://www.vlfeat.org/api/kmeans.html) using the VlFeat implementation of Llloyd's algorithm as well as other faster variants.
###Running K-means
KMeans is a clustering algorithm. Its purpose is to partition a set of vectors into K
 groups that cluster around common mean vector. This can also be thought as *approximating* the input each of the input vector with one of the means, so the clustering process finds, in principle, the best dictionary or codebook to *vector quantize* the data.
Consider a dataset containing 1000 randomly sampled 2D points:
numData = 5000 ;dimension = 2 ;data = rand(dimension,numData) ;

The function [vl_kmeans](http://www.vlfeat.org/matlab/vl_kmeans.html)
 can be used to cluster the data into, say, 30 groups:
numClusters = 30 ;[centers, assignments] = vl_kmeans(data, numClusters);

By default, this uses the the [Lloyd](http://www.vlfeat.org/api/kmeans-fundamentals.html#kmeans-lloyd) algorithm, a method that alternates between optimizing the cluster centers and the data-to-center assignments. Once this process terminates, the matrix centers
 contains the cluster centers and the vector assignments
 the (hard) assignments of the input data to the clusters. The cluster centers are also called *means* because it can be shown that, when the clustering is optimal, the centers are the means of the corresponding data points. The cluster centers and assignments can be visualized as follows:
![](http://upload-images.jianshu.io/upload_images/1174946-7744f637011b325c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)KMeans clustering of 5000 randomly sampled data points. The black dots are the cluster centers.

Given a new data point x
, this can be mapped to one of the clusters by looking for the closest center:
x = rand(dimension, 1) ;[~, k] = min(vl_alldist(x, centers)) ;

For larger datastes, this process may be significantly accelerated by using [KDTrees](http://www.vlfeat.org/overview/kdtree.html) or other approximate nearest neighbor procedures.
Choosing an initialization method
K-means uses local optimization algorithms and is therefore sensitive to initalization. By default, [vl_kmeans](http://www.vlfeat.org/matlab/vl_kmeans.html)
 initializes the cluster centers by picks K
 data points at random. Other initalization strategies can be selected as well. [kmeans++](http://www.vlfeat.org/overview/%dox:kmeans-plus-plus) is a popular method that greedily pick K
 data points that are maximally different, and can be use as follows:
[centers, assignments] = vl_kmeans(data, numClusters, 'Initialization', 'plusplus') ;

Choosing an optimization algorithm
In addition to the original KMeans algorithm proposed by Lloyd, [vl_kmeans](http://www.vlfeat.org/matlab/vl_kmeans.html)
 supports two additional algorithms: [Elkan's](http://www.vlfeat.org/overview/%dox:kmeans-elkan) variant, an exact algorithm using an acceleration technique based the triangular inequality, and [ANN](http://www.vlfeat.org/api/kmeans-fundamentals.html#kmeans-ann), an approximated algorithm using approximate nearest neighbours.
These optimization methods can be enabled by setting the 'Algorithm'
 parameter to 'Lloyd'
, 'Elkan'
 or 'ANN'
 respectively. When using the'ANN'
 algorithm, the user can also specify the parameters 'MaxNumComparisons'
 and 'NumTrees'
 to [configure the KD-tree](http://www.vlfeat.org/api/kdtree.html) used used as ANN. In particular, 'MaxNumComparisons'
 controls the trade-off between approximation quality and speed.
[vl_demo_kmeans_ann_speed](http://www.vlfeat.org/matlab/demo/vl_demo_kmeans_ann_speed.html)
 compares the speed of the three algorithms. Because of the random initialization, each of the KMeans calls converges to a different local minimum in a different amount of iterations. In order to measure more accurately the speed of each pass, a relatively small number of 'MaxNumIterations'
 option) is selected. Note that the speedup factor are in general much more dramatic when truly large datasets are considered.
![](http://upload-images.jianshu.io/upload_images/1174946-fe2bb3a2d929c191.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)Comparisons of Elkan, Lloyd and ANN for different values of MaxNumComparison
, expressed as a fraction of the number of clusters. The figure reports the duration, final energy value, and speedup factor, using both the serial and parallel versions of the code. The figure was generated using [vl_demo_kmeans_ann_speed](http://www.vlfeat.org/matlab/demo/vl_demo_kmeans_ann_speed.html).

from [VLFeat](http://www.vlfeat.org/overview/kmeans.html)