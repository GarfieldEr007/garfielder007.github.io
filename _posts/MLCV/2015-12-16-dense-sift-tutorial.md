---
layout: post
title: Dense Scale Invariant Feature Transform (DSIFT)
date: 2015-12-16
categories: MLCV
tags: [Dense SIFT,特征描述子]
description: Machine Learning相关

---




###Table of Contents
[Overview](http://www.vlfeat.org/api/dsift.html#dsift-intro)
[Usage](http://www.vlfeat.org/api/dsift.html#dsift-usage)
[Technical details](http://www.vlfeat.org/api/dsift.html#dsift-tech)[Dense descriptors](http://www.vlfeat.org/api/dsift.html#dsift-tech-descriptor-dense)
[Sampling](http://www.vlfeat.org/api/dsift.html#dsift-tech-sampling)

>Author:
>
>Andrea Vedaldi
>
>Brian Fulkerson

[dsift.h](http://www.vlfeat.org/api/dsift_8h.html) implements a dense version of [SIFT](http://www.vlfeat.org/api/sift_8h.html). This is an object that can quickly compute descriptors for densely sampled keypoints with identical size and orientation. It can be reused for multiple images of the same size.
Overview
See also
[The SIFT module](http://www.vlfeat.org/api/sift.html), [Technical details](http://www.vlfeat.org/api/dsift.html#dsift-tech)

This module implements a fast algorithm for the calculation of a large number of SIFT descriptors of densely sampled features of the same scale and orientation. See the [SIFT module](http://www.vlfeat.org/api/sift.html) for an overview of SIFT.
The feature frames (keypoints) are indirectly specified by the sampling steps ([vl_dsift_set_steps](http://www.vlfeat.org/api/dsift_8h.html#a42ae6bf77a9b737fd1e45ad5c43263dd)) and the sampling bounds ([vl_dsift_set_bounds](http://www.vlfeat.org/api/dsift_8h.html#a7d34c8e257c873f2ed580b046296d1ac)). The descriptor geometry (number and size of the spatial bins and number of orientation bins) can be customized ([vl_dsift_set_geometry](http://www.vlfeat.org/api/dsift_8h.html#a930f20c25eab08d9490830b0a358ff2b), [VlDsiftDescriptorGeometry](http://www.vlfeat.org/api/structVlDsiftDescriptorGeometry.html)).

![dsift-geom.png](http://www.vlfeat.org/api/dsift-geom.png)

Fig. Dense SIFT descriptor geometry

By default, SIFT uses a Gaussian windowing function that discounts contributions of gradients further away from the descriptor centers. This function can be changed to a flat window by invoking [vl_dsift_set_flat_window](http://www.vlfeat.org/api/dsift_8h.html#a8dfe2d20dbe9885d0c139c5b81b5f4b0). In this case, gradients are accumulated using only bilinear interpolation, but instad of being reweighted by a Gassuain window, they are all weighted equally. However, after gradients have been accumulated into a spatial bin, the whole bin is reweighted by the average of the Gaussian window over the spatial support of that bin. This “approximation” substantially improves speed with little or no loss of performance in applications.
Keypoints are sampled in such a way that the centers of the spatial bins are at integer coordinates within the image boundaries. For instance, the top-left bin of the top-left descriptor is centered on the pixel (0,0). The bin immediately to the right at (binSizeX
,0), where binSizeX
 is a paramtere in the [VlDsiftDescriptorGeometry](http://www.vlfeat.org/api/structVlDsiftDescriptorGeometry.html) structure. [vl_dsift_set_bounds](http://www.vlfeat.org/api/dsift_8h.html#a7d34c8e257c873f2ed580b046296d1ac) can be used to further restrict sampling to the keypoints in an image.
Usage
DSIFT is implemented by a [VlDsiftFilter](http://www.vlfeat.org/api/structVlDsiftFilter.html) object that can be used to process a sequence of images of a given geometry. To use the **DSIFT filter**:
Initialize a new DSIFT filter object by [vl_dsift_new](http://www.vlfeat.org/api/dsift_8c.html#aa9ba7ffaa72c137c457642ce833dab05) (or the simplified [vl_dsift_new_basic](http://www.vlfeat.org/api/dsift_8c.html#aa025e58a852d8df078c6b74b8136c704)). Customize the descriptor parameters by[vl_dsift_set_steps](http://www.vlfeat.org/api/dsift_8h.html#a42ae6bf77a9b737fd1e45ad5c43263dd), [vl_dsift_set_geometry](http://www.vlfeat.org/api/dsift_8h.html#a930f20c25eab08d9490830b0a358ff2b), etc.
Process an image by [vl_dsift_process](http://www.vlfeat.org/api/dsift_8c.html#a09d5525ad7e16e2b9f3f1b9d273c85f6).
Retrieve the number of keypoints ([vl_dsift_get_keypoint_num](http://www.vlfeat.org/api/dsift_8h.html#a3b5fabb1496fc91a70669d4201f47a5b)), the keypoints ([vl_dsift_get_keypoints](http://www.vlfeat.org/api/dsift_8h.html#a0cba85e88ae5232fe74368175a8ba510)), and their descriptors ([vl_dsift_get_descriptors](http://www.vlfeat.org/api/dsift_8h.html#acd5425e9764383a5ef05bce00fd40e94)).
Optionally repeat for more images.
Delete the DSIFT filter by [vl_dsift_delete](http://www.vlfeat.org/api/dsift_8c.html#aa123f1d9e79ab01882646f713dfb4f0c).

Technical details
This section extends the [SIFT descriptor section](http://www.vlfeat.org/api/sift.html#sift-tech-descriptor) and specialzies it to the case of dense keypoints.
Dense descriptors
When computing descriptors for many keypoints differing only by their position (and with null rotation), further simplifications are possible. In this case, in fact,
xh(t,i,j)==mσx^+T,mσ∫gσwin(x−T)wang(∠J(x)−θt)w(x−Txmσ−x^i)w(y−Tymσ−y^j)|J(x)|dx.

Since many different values of *T* are sampled, this is conveniently expressed as a separable convolution. First, we translate by xij=mσ(x^i, y^i)⊤
 and we use the symmetry of the various binning and windowing functions to write
h(t,i,j)T′==mσ∫gσwin(T′−x−xij)wang(∠J(x)−θt)w(T′x−xmσ)w(T′y−ymσ)|J(x)|dx,T+mσ[xiyj].

Then we define kernels
ki(x)kj(y)==12π−−√σwinexp(−12(x−xi)2σ2win)w(xmσ),12π−−√σwinexp(−12(y−yj)2σ2win)w(ymσ),

and obtain
h(t,i,j)J¯t(x)==(kikj∗J¯t)(T+mσ[xiyj]),wang(∠J(x)−θt)|J(x)|.

Furthermore, if we use a flat rather than Gaussian windowing function, the kernels do not depend on the bin, and we have
k(z)h(t,i,j)==1σwinw(zmσ),(k(x)k(y)∗J¯t)(T+mσ[xiyj]),

(here σwin
 is the side of the flat window).
Note
In this case the binning functions k(z)
 are triangular and the convolution can be computed in time independent on the filter (i.e. descriptor bin) support size by integral signals.

Sampling
To avoid resampling and dealing with special boundary conditions, we impose some mild restrictions on the geometry of the descriptors that can be computed. In particular, we impose that the bin centers T+mσ(xi, yj)
 are always at integer coordinates within the image boundaries. This eliminates the need for costly interpolation. This condition amounts to (expressed in terms of the *x* coordinate, and equally applicable to *y*)
{0,…,W−1}∋Tx+mσxi=Tx+mσi−Nx−12=T¯x+mσi,i=0,…,Nx−1.

Notice that for this condition to be satisfied, the *descriptor* center Tx
 needs to be either fractional or integer depending on Nx
 being even or odd. To eliminate this complication, it is simpler to use as a reference not the descriptor center *T*, but the coordinates of the upper-left bin T¯
. Thus we sample the latter on a regular (integer) grid
[00]≤T¯=[T¯minx+pΔxT¯miny+qΔy]≤[W−1−mσNxH−1−mσNy],T¯=⎡⎣Tx−Nx−12Ty−Ny−12⎤⎦

and we impose that the bin size mσ
 is integer as well.

from [VLFeat](http://www.vlfeat.org/api/dsift.html).