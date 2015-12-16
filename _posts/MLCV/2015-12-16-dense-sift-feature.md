---
layout: post
title: 计算机视觉快速特征描述子Dense SIFT
date: 2015-12-16
categories: MLCV
tags: [Dense SIFT,特征描述子]
description: Machine Learning相关

---


![Dense SIFT.png](http://upload-images.jianshu.io/upload_images/1174946-87a7914a8274b357.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

VLFeat implements a [fast dense version of SIFT](http://www.vlfeat.org/api/dsift.html), called [vl_dsift](http://www.vlfeat.org/matlab/vl_dsift.html)
. The function is roughly equivalent to running SIFT on a dense gird of locations at a fixed scale and orientation. This type of feature descriptors is often uses for object categorization.
###Dense SIFT as a faster SIFT
The main advantage of using [vl_dsift](http://www.vlfeat.org/matlab/vl_dsift.html)
 over [vl_sift](http://www.vlfeat.org/matlab/vl_sift.html)
 is speed. To see this, load a test image
I = vl_impattern('roofs1') ;I = single(vl_imdown(rgb2gray(I))) ;

To check the equivalence of vl_disft
 and [vl_sift](http://www.vlfeat.org/matlab/vl_sift.html)
 it is necessary to understand in detail how the parameters of the two descriptors are related.
**Bin size vs keypoint scale**. DSIFT specifies the descriptor size by a single parameter, size
, which controls the size of a SIFT spatial bin in pixels. In the standard SIFT descriptor, the bin size is related to the SIFT keypoint scale by a multiplier, denoted magnif
 below, which defaults to 3
. As a consequence, a DSIFT descriptor with bin size equal to 5 corresponds to a SIFT keypoint of scale 5/3=1.66.

**Smoothing.** The SIFT descriptor smoothes the image according to the scale of the keypoints (Gaussian scale space). By default, the smoothing is equivalent to a convolution by a Gaussian of variance s^2 - .25
, where s
 is the scale of the keypoint and .25
 is a nominal adjustment that accounts for the smoothing induced by the camera CCD.

Thus the following code produces equivalent descriptors using either DSIFT or SIFT:
binSize = 8 ;magnif = 3 ;Is = vl_imsmooth(I, sqrt((binSize/magnif)^2 - .25)) ;[f, d] = vl_dsift(Is, 'size', binSize) ;f(3,:) = binSize/magnif ;f(4,:) = 0 ;[f_, d_] = vl_sift(I, 'frames', f) ;

The difference, of course, is that DSIFT is much faster.

![](http://upload-images.jianshu.io/upload_images/1174946-d37ff13771df6ecb.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

![](http://upload-images.jianshu.io/upload_images/1174946-5f3776040db78a26.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Left: accuracy of the slow and fast dense SIFT implementations in [vl_dsift](http://www.vlfeat.org/matlab/vl_dsift.html) compared to the SIFT baseline from vl_sift
. Right: speedup. The fast version is less similar to the original SIFT descriptors but from 30 to 70 times faster than SIFT. Notice that the equivalence of the descriptors does not necessarily indicate that one would work better than the other in applications.

PHOW descriptors
The PHOW features [[1]](http://www.vlfeat.org/overview/dsift.html#ref1) are a variant of dense SIFT descriptors, extracted at multiple scales. A color version, named PHOW-color, extracts descriptors on the three HSV image channels and stacks them up. A combination of [vl_dsift](http://www.vlfeat.org/matlab/vl_dsift.html)
 and [vl_imsmooth](http://www.vlfeat.org/matlab/vl_imsmooth.html)
 can be used to easily and efficiently compute such features.
VLFeat includes a simple wrapper, [vl_phow](http://www.vlfeat.org/matlab/vl_phow.html)
, that does exactly this:
im = vl_impattern('roofs1') ;[frames, descrs]=vl_phow(im2single(im)) ;

Note that this typically generate a very large number of features. In this example, there are 162,574 features.
References
[1] A. Bosch, A. Zisserman, and X. Munoz. *Image classifcation using random forests and ferns.* In Proc. ICCV, 2007.

from [VLFeat](http://www.vlfeat.org/overview/dsift.html).














