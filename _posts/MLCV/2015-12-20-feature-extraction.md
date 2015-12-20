---
layout: post
title: Finding more duplicate icons – An introduction to image feature extraction
date: 2015-12-20
categories: MLCV
tags: [VLFeat,SVM]
description: Machine Learning相关

---




Authors: Radu Ciocoiu & Silviu Tantos

Following a small experiment in the spring on detecting duplicate icons. We wanted to dive deeper into this field. One of the main task in finding identical icons, is that they are most often not digital duplicates, but still look identical. This challenge can be partly overcome by using a technique called feature extraction. Let me explain…

I’ll first start with what this text is and what it is not, it is a brief introduction to feature extraction written from the point of a beginner. It doesn’t dive into algorithms or what my designer colleagues sometimes refer to as ‘magic’. And any feedback, corrections or additions are more than welcomed. Just leave a comment bellow.

What are features?

An image feature is a general term but it usually means a part of an image that contains interesting details or a property of the image which we are interested in. What are ‘interesting details’? It depends on the overall goal and what the application is trying to achieve. Many computer vision algorithms use feature detection as the initial step and a large number of feature detectors have been developed. For example, some of the most commonly used features are:

Edges

http://blog.iconfinder.com/wp-content/uploads/2014/10/canny.png

Image before and after applying edge detection

Edges are points that are at the boundary of two image regions and are detected by computing the change in brightness, we can say that we have an edge where there is a rapid change in brightness. Usually the algorithm implementation puts some some constraints in place for the on the properties of an edge, for example the minimum length for it to be considered one, shape, smoothness, and gradient value. http://blog.iconfinder.com/wp-content/uploads/2014/10/edge.png

Zooming in we can see the luminosity change where the two regions meet and the edge is formed.

They can be used to find the boundaries of an object or a surface and they also significantly reduce the amount of data needed to be processed while preserving the details that we are interested in an image. Examples of edge detection algorithms: Sobel, Canny, Gabor, Kirsch, Prewitt.

Corners/interest points

http://blog.iconfinder.com/wp-content/uploads/2014/10/harris.png

Detected interest points using Harris corner detection marked in green.

A corner is the point located at the intersection of two edges and you can think of an interest point as a small region in the image (window) for which no matter in which neighboring direction you look there is a high variations in brightness. This means that an interest point can be a corner sometimes. In practice the terms are used interchangeably and most corner detection algorithms actually detect interest points rather than corners as they are far more useful.

http://blog.iconfinder.com/wp-content/uploads/2014/10/harris_diagram.png
http://blog.iconfinder.com/wp-content/uploads/2014/10/corner.png

Zooming in we can see the brightness changes in the neighboring regions.

What makes a good interest point is the ability to recognise that point at that same location, even if the image is resized, rotated, the brightness changes or the image was taken from a slightly different point of view. Examples of edge detection algorithms: Harris, SUSAN, Shi & Tomasi, FAST.

Blobs/regions of interest

http://blog.iconfinder.com/wp-content/uploads/2014/10/blob.png

Detected largest blob highlighted in green.

Blobs, or regions of interest, are regions where the brightness or color of the points change very little so they can be considered in some sense to be similar to each other. Examples of blob detection algorithms: FAST, Laplacian of Gaussian, Difference of Gaussians, Determinant of Hessian, MSER, PCBR.

Color

Color can hold sometimes a lot of information, Lego Image is the perfect example of that, the creative artist Jung Von Matt show how much information can be depicted by using just colors of familiar cartoon characters.

http://blog.iconfinder.com/wp-content/uploads/2014/10/lego_southpark.jpeg

Southpark characters made with Lego. Artist: Jung Von Matt

A good example of dominant color extraction can be found on the pyimagesearch blog.

Computer vision steps

http://blog.iconfinder.com/wp-content/uploads/2014/10/computer_vision_flow.png
Pre-processing

This is usually the first step before any computer vision methods can be applied, it usually includes steps such as:

Gray-scaling to reduce the amount of , we will only have to examine one value (light intensity) instead of three (red, green, blue color intensity).
Blurring to remove sensor noise and speckles from the image so that it does not introduce false information when detecting. Speckles can be for example falsely detected as corners.
Contrast enhancement to assure that relevant information can be detected.
Rescaling to reduce the amount of processing work needed to be done. For example in an 1920-by-1080 image we will have 2073600 values instead of 480000 values for an 800-by-600 image.
Feature detection

Feature detection is a low-level image processing operation and usually comes after the pre-processing step and it examines every pixel to see if the region around that pixel could be used as a feature. Feature detection can also be a sub-step in a larger algorithm, then the algorithm will typically only examine the image in the region of the features.

Feature description

Once the features that are interesting to us have been detected, they can be extracted. The result is known as a feature descriptor or feature vector and they characterize the region around the key point as rotation and luminosity invariance vectors. They can also reduce the amount of data required to describe the image region that corresponds to the feature, they are represented as N-element vector in another domain and two descriptors can be compared using a distance metric, the less this distance – the more similar descriptors are. One example of descriptor is the HOG (Histogram of Oriented Gradients) descriptor, such are SIFT and SURF descriptors. These are computed based on the gradients orientation and expressed as vectors. Practical example: We can find a corner with the Harris corner detection method, and we can describe it with any method we want (Histograms, HOG, Local Orientation for example).

Matching/indexing/recognition

Given that a descriptor has been created for each identified key point we can now process and make decisions based on them. We could, for example, make matches by comparing our descriptors with a known descriptor set stored in a database (OCR, facial recognition, object recognition) or compare the descriptors directly between two images to find matches.

http://blog.iconfinder.com/wp-content/uploads/2014/10/orb_matches.png

Matched descriptors from one image to another.

Next step

This post was meant as a general introduction to the terms used in the computer vision world. In the next post we are gonna take a few practical examples and see show we can create a content based image retrieval system step by step.

Further reading

If this subject caught your interest, you should check out some of these articles.

http://en.wikipedia.org/wiki/Feature_(computer_vision)
http://en.wikipedia.org/wiki/Feature_detection_(computer_vision)
http://en.wikipedia.org/wiki/Computer_vision
http://crcv.ucf.edu/courses/CAP5415/Fall2012/Lecture-1-CVIntroduction.pdf
http://cs.brown.edu/courses/cs143/
http://www.societyofrobots.com/programming_computer_vision_tutorial.shtml
http://www.scholarpedia.org/article/Scale_Invariant_Feature_Transform#Image_descriptor

from [VLFeat](http://www.vlfeat.org/overview/svm.html#tut.svm).