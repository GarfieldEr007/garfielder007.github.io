---
layout: post
title: VLFeat教程SVM
date: 2015-12-17
categories: MLCV
tags: [VLFeat,SVM]
description: Machine Learning相关

---




**VLFeat** includes fast SVM solvers,SGC [1] and (S)DCA [2], bothimplemented invl_svmtrain
. The function also implementsfeatures, like Homogeneous kernel map expansion and SVM onlinestatistics. (S)DCA can also be used with different loss functions.
###Support vector machine
A simple example on how to usevl_svmtrain
ispresented below. Let's first load and plot the training data:

```
% Load training data X and their labels yvl_setup demo % to load the demo dataload('vl_demo_svm_data.mat');Xp = X(:,y==1);Xn = X(:,y==-1);figureplot(Xn(1,:),Xn(2,:),'*r')hold onplot(Xp(1,:),Xp(2,:),'*b')axis equal ;
```

Now we have a plot of the tutorial training data:

![](http://upload-images.jianshu.io/upload_images/1174946-ba973ff17479c930.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

Training Data.  

Now we will set the learning parameters:

```
lambda = 0.01 ; % Regularization parametermaxIter = 1000 ; % Maximum number of iterations
```
Learning a linear classifier can be easily done with the following 1line of code:

```[w b info] = vl_svmtrain(X, y, lambda, 'MaxNumIterations', maxIter)
```
Now we can plot the output model over the trainingdata.

```
% Visualisationeq = [num2str(w(1)) '*x+' num2str(w(2)) '*y+' num2str(b)];line = ezplot(eq, [-0.9 0.9 -0.9 0.9]);set(line, 'Color', [0 0.8 0],'linewidth', 2);
```

The result is plotted in the following figure.

![](http://upload-images.jianshu.io/upload_images/1174946-e9e550c416818687.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

Learned model.  

The outputinfo
is a struct containing some statistic on the learned SVM:

```
info = solver: 'sdca' lambda: 0.0100 biasMultiplier: 1 bias: 0.0657 objective: 0.2105 regularizer: 0.0726 loss: 0.1379 dualObjective: 0.2016 dualLoss: 0.2742 dualityGap: 0.0088 iteration: 525 epoch: 3 elapsedTime: 0.0300
```

It is also possible to use under some assumptions [3] a homogeneous kernel map expanded online inside the solver. This can be done with the following commands:

```
% create a structure with kernel map parametershom.kernel = 'KChi2';hom.order = 2;% create the dataset structuredataset = vl_svmdataset(X, 'homkermap', hom);% learn the SVM with online kernel map expansion using the dataset structure[w b info] = vl_svmtrain(dataset, y, lambda, 'MaxNumIterations', maxIter)
```

The above code creates a training set without applying any homogeneous kernel map to the data. When the solver is called it will expand each data point with a Chi Squared kernel of period 2.
###Diagnostics
VLFeat allows to get statistics during the training process. It is sufficient to pass a function handle to the solver. The function will be then called everyDiagnosticFrequency
time.
(S)DCA diagnostics also provides the duality gap value (the difference between primal and dual energy), which is the upper bound of the primal task sub-optimality.

```
% Diagnostic functionfunction diagnostics(svm) energy = [energy [svm.objective ; svm.dualObjective ; svm.dualityGap ] ] ;end% Training the SVMenergy = [] ;[w b info] = vl_svmtrain(X, y, lambda,... 'MaxNumIterations',maxIter,... 'DiagnosticFunction',@diagnostics,... 'DiagnosticFrequency',1)
```

The objective values for the past iterations are kept in the matrixenergy
. Now we can plot the objective values from the learning process.

```
figurehold onplot(energy(1,:),'--b') ;plot(energy(2,:),'-.g') ;plot(energy(3,:),'r') ;legend('Primal objective','Dual objective','Duality gap')xlabel('Diagnostics iteration')ylabel('Energy')
```

![](http://upload-images.jianshu.io/upload_images/1174946-4c7531e8b98673d7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

SVM objective values plot.  

###References
[1] Y. Singer and N. Srebro. *Pegasos: Primal estimated sub-gradient solver for SVM*. In Proc. ICML, 2007.
[2] S. Shalev-Schwartz and T. Zhang. *Stochastic Dual Coordinate Ascent Methods for Regularized Loss Minimization*. 2013.
[3] A. Vedaldi and A. Zisserman. *Efficient additive kernels via explicit feature maps*. In PAMI, 2011.

from [VLFeat](http://www.vlfeat.org/overview/svm.html#tut.svm).