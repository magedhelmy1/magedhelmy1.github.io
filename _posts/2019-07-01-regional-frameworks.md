---
title: Region Proposal Based Framework for Object Detection
author: Maged Helmy
date: 2019-07-01 14:00:00 +0100
categories: [Blogging, Deep Learning]
tags: [computer_vision, deep_learning]
---

### Abstract

The goal of this essay is to describe the top 7 promising approaches in generic object detection of still images including the problem they aim to tackle, the methodology applied, the results and to discuss these approaches. We start off by briefly introducing object detection and then dive into the description of the selected architectures.

## 1.	Introduction

Object detection architecture aims to estimate the location and the label of an object in an image [1]. Object detection techniques can generally be split into two distinct categories. Firstly, the two-step method aims to first locate the object in the image (object localization) and then estimates the category of the object (object-classification) [2]. These architectures can be referred to as the Region Proposal Based Framework. Secondly, the one-step method directly aims to locate and categorize the objects at one go. These architectures are known as the Unified Framework [3]. The topic of this essay will describe 7 selected architectures from the Region Proposal Based Framework.

Object Localization can be further subdivided into 3 categories. Generic object detection which is a bounding box around the location of an object [4], semantic segmentation which is a pixel-wise segmentation mask around the object(s) from the same class [5], and instance segmentation which is a pixel-wise segmentation mask around an individual object regardless of its class [6].

Object Classification can be further generalized into two categories; object matching which detects specific instances of the object localized (i.e. Oslo Town Hall, Norwegian Parliament), and generic object detection which is detecting the category of the objects localized (i.e. Skyscraper, Dog, Cat) [7]. The latter is more challenging due to the large variations of appearance differences within the same category, for example, the amount of light on the image, the object positioning, rotation angle, if the object is mirrored, occlusion, distance from the camera, resolution, blur, motion. [8]. Furthermore, existing object detection architectures have been tweaked for domain-specific object detection cases like pedestrian detection [9], face detection [10], salient object detection [11], medical image analysis [12], vehicle detection [13] and text detection [14] however in this article we will focus on generic object detection architecture of those techniques.

Generally, all architectures compete on the Mean Average Precision (mAP) and their efficiency (Speed of detection per frame) in a given dataset [4], [15]. Different architectures accuracies have been compared by the authors and others on the most popular datasets for object recognition like PASCAL VOC (2012)- 11,540 images and 20 categories [4], ImageNet 14 million+ images and 21,841 categories [16], MS COCO 328,000+ images and 91 categories[6], Places 10 million+ images and 434 categories[17] and Open Images with 9 million+ and 6000+ categories [18].

In the following table, we summarize the frameworks that achieved breakthroughs after the Deep Convolutional Neural Network era that started in 2012 [19] [2]. The former era was dominated by the Scale Invariant Feature Transform technique (SIFT) from 1999 to 2012 [20].

xxxxxx
Table 1.

Other image classifications and object detections include and are not limited to NOC, Bayes, MR-CNN&S-CNN, HyperNet, ION, MSGR, StuffNet, OHEM, SDP+CRC , SubCNN, GBD-Net, PVANET, NIN, GoogLeNet, VGGNet, ResNet, DenseNet, RetinaNet, ResNet, Corner Net, Inception, Hourglass, Dilated Residual Networks, Xception, VGG, DetNet, Inception, Dual Path Networks (DPN), FishNet, ResNeXt, and GLoRe [3], [7], [22].

In the subsequent sections, we select 7 algorithms from Region Proposal Framework and will adhere to the following style to describe the selected papers on this topic.

Paper Name -> Problem -> Description -> Method (Input, Output, Architecture, Loss) -> Results -> Discussion.
## 2.	Region Proposal Based Framework

## Paper 1: Rich feature hierarchies for accurate object detection and semantic segmentation [21]

### Problem
When this paper was released in 2014, the best performing object detection architectures have plateaued for from 2010 to 2012 with an accuracy of ~35% on the most popular datasets [19]. This algorithm has achieved a ~20% higher accuracy than its predecessor on the VOC 2012 dataset [21]. This method was termed Regions with CNN features or R-CNN. It is also one of the first methods that propose a two-step approach, and many subsequent methods were based on this approach from 2014 to this day [22].

### Description
Region proposal frameworks are inspired by the combination of DCNN [2] and region proposals [23]. R-CNN takes in an image, applies a segmentation mask to it and extracts the top ~2000 promising bounding box on that segmentation. The bounding boxes are of different scales which increases the probability of identifying different sizes of shapes. It then computes the features of these boxes using a CNN and classifies each region with a linear SVM. On the other hand, this method can be slightly adjusted if the training data is low, and is to apply a supervised pre-training CNN on the ImageNet followed by fine-tuning of the low training data.

### Method
The RCNN consists of two concurrent pipelines, the region detector, and the object detector. For the region detector, RCNN takes in an image and applies a non-deep learning model called Selective search to extract approx 2000 regions of interest (RoI). These regions present the places in the image where an object is more likely to reside. The proposed region is then warped or cropped to fit a specific dimension before passed into the object detector. The object detector applies CNN + max-pooling with an activation function to calculate the feature map. The feature map is then passed to a two fully connected layer to create a 4096-dimensional vector. This vector is passed to a classification head that tries to figure out the class, and the regression network which tries to refine the coordinates of the box. The classification head is optimized using cross-entropy loss while the regression head is refined using L2 loss. The model is trained by first optimizing the model on the classification loss then the regression loss. This can take up to several days, with intense storage space since all the features computed from the proposed regions require many gigabytes of space.

To summarize the steps:
With sufficient training labels, this paper methodology consists of three modules.

1)	Generating the region proposals: Selective search method is used to suggest the regions
2)	Extracting the features using CNN: A 4096-dimensional vector is extracted from each region generated by the previous step using the method applied by the DCNN [2]. The features are then computed by subtracting the mean from a 227 by 227 image through a five convolutional layer and a two fully connected layer. The output region is warped equally with p=16 however the paper suggests that alternative values can be used.
3)	Extracting the class using SVM: Each region is scored using an SVM, and a greedy non-maximum suppression for each class is applied independently on the proposed region. If the 2 regions have an intersection-over-union (IoU) higher than a threshold, one region will be rejected.

If there is a lack of training set, the paper suggests the addition of these two modules:

1)	Supervised pre-training: They start by training the CNN on one of the large datasets as an image classification problem using Caffe CNN library.
2)	Domain-specific fine-tuning: The wrapped regions created from step two from the above method is used to fine-tune the CNN parameters using stochastic gradient descent.


### Results
The paper applies the results on the PASCAL VOC 2007 dataset and 2010-12 which archives a 53.7 % mAP and 53.3% respectively, which is a big jump from the previous algorithm of mAP 35.1% from the algorithms at that time.

### Discussion
R-CNN is a big step towards building a high-quality object detection architecture post the SIFT era and in the DCNN era. This is noticeable in the jump of accuracy introduced by the R-CNN. However, there are some drawbacks to using R-CNN. Firstly, the R-CNN has multi-stage multi-steps modules that all need to be optimized individually to get good results. This increases the chances of introducing inaccuracies and makes training time notably longer. Secondly, R-CNN uses a fully connected layer that requires a fixed input shape, in our methodology above we highlight it must be for example 227 x 227, which means the CNN part has to re-compute on the regions to ensure it fits that size adding time to training and testing. Finally, the regions extracted are approximately 2000 which one can argue in sparse images are way too much, and in denser images are way too little.

Such disadvantages have led to the development of successors such as SPPNet, Fast RCNN, Faster RCNN, R-FCN, FPN, and Mask R-CNN.


## Paper 2: Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition [24]

### Problem
As highlighted in the abstract of the paper, this method introduces two changes to the existing R-CNN architecture. First, it aims to tackle the challenge of having a fixed-size window for the fully connected layer by forcing arbitrary images to fit into this window via cropping or warping since important information can be lost or distorted leading to the reduction of accuracy. Secondly, SPPnet computes the feature maps for the image ones instead of repeatedly computing it on each RoI region as the R-CNN.

### Description
An important question arises which is: why does the CNN part of the RCNN architecture require a fixed shape? To break this down, a CNN has two layers, the convolutional layer, and the fully connected (FC) layer. The convolutional layer actually does not need a fixed image input and can generate feature maps from any image size since it operates in a sliding-window manner. However, the FC layers require a fixed input thus introducing this constraint. This paper introduces the Spatial Pyramid Pool to tackle this challenge by adding it to the top of the last convolutional layer before the FC layer. So instead of cropping or warping the image, this method aggregates the information by pooling the features and feeding it to the FC layer. The spatial pyramid pooling is an extension of the Bag-of-Words model released in 2006 [25]. The spatial pyramid pooling allows the passing of any image scale/size to the FC layer without having to warp or crop the image.

### Method
The difference between the RCNN method and the spatial pyramid pooling methods can be illustrated as follows; The RCNN takes in an image, applies crop/warp, passes it to the conv layer and then the FC layer. The SPPnet method takes in an image and passes it directly to the conv layer, applies the spatial pyramid pooling then passes it to the FC layer. The SPP takes in the feature maps from the last layer of the convolutional layer (5th layer) to create feature maps of fixed-length feature vectors regardless of the input image size.

To summarize, SPPnet calculates a feature map for the whole image, and then classifies the regions using a feature vector. The features are then extracted using max-pool. Images with different sizes can be pooled and aggregated into a spatial pyramid which is then passed to the FC layer.

### Results
When this paper was released, four existing object detection architectures were compared with their non-spp counterparts (ZF-5, Convnet*-5, Overfeat-5, Overfeat-7) and the CNN with SPP has shown state-of-the-art classification results on Pascal VOC 2007 and ranked #2 on the ILSVRC 2014 competition [22].

### Discussion
The spatial pyramid pooling method is more efficient than its predecessor since it obtains a significant speedup. The speedup is due to the fact that the CNN layer can run ones on the test image to generate a feature map that can then be passed on to the FC layer. Furthermore, it is more accurate since it can learn feature maps from any scale without losing information to cropping or warping. The Multi-level pooling makes the input images more robust to deformation. The main drawbacks of SPP-net are that it is still a multi-stage, multi-step pipeline (feature extraction, network fine-tuning, SVM training, bounding box regressor, feature caching) still making it relatively slow. Furthermore, the authors of the paper mention that the accuracy of SPP-net layers drops when using deeper CNN since tuning the network will not update the layers before the SPP layer leading to reduced accuracies, and a very difficult challenge in implementing back-propagation.




Figure 1. Paper 1- RCNN




Figure 2. Paper 3-  Fast RCNN










## Paper 3: Fast R-CNN [26]

### Problem
This paper aims to address the problems that arise from the SPPnet and R-CNN architectures. To the date of the publication of this paper in 2015, object detection methods required first, to generate several hundred regions known as “proposals” to generate a feature map, second, the proposals generated were an estimate of the localization. These two joint challenges reduced speed and accuracy and increased complexity.

### Description
Similar to the RCNN, this method uses selective search to find the regions, then passes it to the object detector. It also consists of two SVM heads, one for classification to get the class category, and second regression to calculate the bounding box coordinates. The difference is, instead of running the CNN several times on the RoI, it runs it only once by introducing ROI pooling. Second, it makes the process more streamlined on the object detector side where it jointly classifies and learns the location of the object at the same time by using the multiclass loss. This method generally has a higher mAP achieved by having a single-stage for the training with a multi-task loss. The increased accuracy is obtained by updating all the layers. The speed is achieved by not requiring to cache the features and due to the fact that Fast RCNN learns the softmax classifier and bounding box regression together rather than in two separate processes. These improvements have led to a major decrease in storage space needed.

### Method
Different from the RCNN, Fast-RCNN creates a feature map from the entire image. The feature map of this method is produced by applying convolutional neural networks and max-pooling to the input image. The regions are then cropped using ROI pooling from the feature map instead of the input image. The RoI pooling layer converts the features of the proposals into a feature map. An RoI is a rectangular window that is similar (one pyramid level) but not identical to the Spatial Pyramid Pooling layer used in SPPnets. The cropping on the feature map is based on obtained using selective search (RoI). The cropped regions are passed to a CNN where the output is a fixed-length feature vector 4078 dimensional. These vectors are individually fed into the FC layer, which in turn gives two outputs, 1) softmax probability estimates over the classes and 2) 4 real-values which encode the bounding box position for one of the classes.

### Results
This method improves efficiency in comparison to the SPP-net in training 3x and testing 10x. In comparison to R-CNN, the authors report that “...Fast R-CNN trains 9x faster than R-CNN on the VGG-16 and 213x faster at test-time, with a higher mAP on the PASCAL VOC 2007, 2010 and 2012 dataset….” [26]. These speed improvements are because of a single process that updates all layers without requiring feature caching. The main results are state of the art mAP on PASCAL 200.


### Discussion

One important improvement that this method introduces is the increase in back-propagation efficiency. Previously, RCNN and SPPnet were inefficient since the input to the network layer came from different images, and the region of interest might span the whole image. This method allows the computational sharing of ROIs from the same image due to the fact that regions are applied on the feature map instead of the full image. Moreover, to reduce the time spent on the FC layers, Fast-RCNN uses a truncated singular value decomposition (SVD) to accelerate the testing procedures [27].

This method has significantly increased the speed and efficiency of object detection. Firstly, by streamlining the whole process, and secondly by applying SVD on the testing set. Thus, Fast RCNN is more of a speed improvement than accuracy improvement. On the same dataset that took 84 hours to train, Fast RCNN performed it in 9 hours. A major drawback is that Fast RCNN still relies on external region proposals that make the whole process relatively slow. It uses the selective search method to find the RoI. Furthermore, later research conducted has concluded that convolutional layers are sufficient enough to localize objects, therefore adding an FC layer slows down the process unnecessarily.



Figure 3. Faster RCNN





## Paper 4: Faster r-cnn: Towards real-time object detection with region proposal networks [28]

### Problem
Optimizations introduced by SPP and Fast R-CNN have exposed the fact that using external region proposal methods slows down the process. Previous networks mainly rely on Selective Search (SS) [23] and Edge box [29] to create region proposals. This paper introduces Region Proposal Network (RPN) which aims to replace the SS and Edge box. The RPN introduces an almost cost-free computation for proposal computation.

### Description
Faster R-CNN is RPN + Fast R-CNN. For RPN to compete with methods like selective search, RPN has to predict RoI of multiple scales and ratios from an image much faster. Thus RPN introduced a novel concept of creating anchors on the feature maps. The RPN layer takes in the feature map and generates rectangular object bounds using CNN which are the new “regions of interest”. The RPN is then added to the feature map. Faster R-CNN can be trained end to end like Fast R-CNN. The RPN output basically tells the Fast R-CNN part where to look.

### Method
The faster RCNN architecture is complex because it has several parts that are interconnected to each other. The RPN first initializes anchors of different ratios and scales on the feature maps created by the Conv layer. The author of the paper uses 9 types of anchors when the RoI is decided on. The anchors are off 3 scales and 3 ratios. These anchors are mapped and fed into the two FC layers where one layer is responsible for the category classification and the second for the box regression. RPN shares the convolutional feature with the fast RCNN enabling the same efficient computation as mentioned in the methodology of the previous paper.

### Results
On the VGG-16 model [19], the Faster-RCNN efficiently performs on a 5fps with all steps with an accuracy exceeding all recorded results on the VOC 07 dataset with 73.2% mAP and VOC 12 of 70.4% mAP.

### Discussion
In parallel to the impressive results Faster R-CNN has achieved, two researchers independently challenge the use of Selecting Search and Edge box to propose regions. They concluded that the use of CNN is sufficient to accurately predict the regions without the use of any Selective search or edge box-like methods [30]. Although this method is several times faster than Fast-RCNN, it still relies on applying several hundred of ROIs per image in order to detect the region of interest. This leads to computations not being shared after the ROI layer and thus reducing the overall efficiency of this method.


## Paper 5: R-FCN: Object Detection via Region-based Fully Convolutional Networks [31]

### Problem
In a traditional sense, Faster R-CNN generated regions using RPN first, then ROI pooling and passing it to the FC layer. The processes that came after the ROI pooling were not shareable, meaning that these steps had to be reapplied for each ROI. In R-FCN, the RPN region proposals exist, but different from the R-CNN, the FC layers after the pooling are removed. This prevents having learnable layers after the pooling allowing computational sharing of the network. Moreover, in Faster RCNN, each region proposal had to be cropped and resized to be fed into the Fast RCNN network. The RFCN attempts to speed up the network by converting this process into fully convolutional. It aims to swap the costly per-region subnetworks with a folly convolutional one thus allowing the computation to be shared across the whole image. Moreover, the authors of the paper aim to tackle the dilemma between invariance in image classification and  the variance for object detection brought by GoogLeNets[32] and Residual Nets (ResNets) [33]

### Description
The RFCN differs from the Faster RCNN in the Region of Interest Pooling layer. The RFCN proposes a method to use convolutional layers to create an RoI sub-network. The authors adopt the two-stage object detection since they claim it is more accurate than the unified framework method. It uses the RPN introduced in the previous method to extract features and passes it on the R-FCN. The R-FCN then aggregates the output of the last convolutional layer and generates the scores for each ROI. Selective pooling is then conducted creating a score-map. So instead of cropping the regions from the feature map, the R-FCN inputs the feature map into the regression and classification heads which creates an RoI map on the feature map.

### Method
R-FCN uses ResNet-101 as its backbone of its architecture [33]. The ResNet-101 has 100 convolutional layers with a 1000 FC layer. The average pooling layer and the convolutional layers are removed, and the convolutional layer is used to compute the feature maps. A layer is applied to the last convolutional block to generate the score maps. A sibling convolutional layer is also applied to calculate the bounding box regression.

### Results
On the PASCAL VOC 2007, it achieves an 83.6% mAP with the 101-layer ResNet. Thus suggesting the same accuracy as the Faster RCNN however it achieves that with a 20x the speed for its Faster RCNN counterpart.

### Discussion
In basic terms, the RFCN is a Faster-RCNN which is fully convolutional. This introduces two advantages, and that is CNN is faster than FC layers. Second, the network becomes scale invariant since there is no FC to restrict the input image size.


## Paper 6: Feature pyramid networks for object detection [34]

### Problem
This method was designed to address an issue with Faster RCNN. Faster RCNN was generally made to address the scale-invariant problem introduced by Fast RCNN.  The Faster RCNN takes in an input image and resizes it accordingly. This means that the network had to run on the image several times with different box sizes making it slow. The Feature Pyramid Network (FPN) deals with these different scales while maintaining the speed. The FPN is an extension of Faster RCNN, in the same manner that R-FCN is an extension of the Faster RCNN.

### Description
Having a robust scale invariance is important for object detection since the network should be able to recognize an object at any distance from the camera. The Faster RCNN aimed to tackle this issue by creating anchor boxes. This proved to be time-consuming since the anchor-boxes had to be applied to each RoI. The FPN however, creates multiple feature maps that aim to represent the image at different scales. Hence, the feature map in RPN is replaced by the FPN removing the necessity of having multi-scale anchor boxes. The regression and classification are applied across these multiple feature maps.

### Method
The FPN takes in an input image and outputs multiple feature maps representing smaller height and width but deeper channels known as the bottom-up pathway. Similar to this method is what is mentioned in the ResNet paper where they use fives scales. The author of FPN uses four and neglects the first since it occupies a lot of space. These feature maps represent the anchor. These feature maps go through a 1 by 1 convolutional layer with a depth of 256. The lateral connection is then applied which adds the feature elements to the upsampled version of the feature map. Faster RCNN runs on each scale and predictions for each scale are generated. FPN is made up of two paths, the bottom-up which uses ResNet and the top-down. In the bottom-up approach, CNN is applied to extract features. On the top-down pathway, the FPN constructs a higher resolution layer but the object locations are no longer accurate due to the down and upsampling. Therefore, FPN adds a lateral connection between the constructed layers to increase the probability of predicting locations.

### Results
This method still runs at 5 FPS as benchmarked by the previous methodology with a state of art result on the COCO 2016 dataset. The FPN - Faster R-CNN is faster than its Faster-RCNN counterpart.

### Discussion
Images have objects with different scales which makes it challenging to detect them. Using several anchor boxes to detect objects with different scales and the ratio seems to be memory and time-consuming. FPN seems to push the accuracy boundaries by introducing a pyramid of feature maps to detect objects of different sizes and scales in an image. It is important to highlight that FPN is a feature detector and not an object detector. Therefore FPN has to be used coupled with an object detector with its RoI.


## Paper 7: Mask-RCNN [35]

### Problem
This method extends Faster R-CNN by adding another layer to predict the object mask in parallel with the existing bounding box layer. This is a framework that enables instance segmentation on a state-of-art level.

### Description
The mask branch added to the Faster R-CNN is a small FCN applied to each RoI which predicts on a pixel-to-pixel basis. This method is as equally fast as the Faster-RCNN. Briefly, the Faster R-CNN had two stages, the RPN and the Fast R-CNN combined. The Mask RCNN adopts the same notion with an identical first stage of RPN, and in the second stage, it outputs a mask for each ROI in parallel to the predicting class and box. The branch added to the second layer is an FCN on top of a CNN feature map. The ROI poolings lead to misalignment, therefore the RoIAlign layer is proposed to preserve the pixel level alignments.

### Method
The main method Mask-RCNN introduces is the RoIAlign which preserves the pixel spatial correspondences. It replaces the quantization from the RoI pooling with bilinear interpolation. In the first stage, an RPN scans the feature maps of the FPN and proposes regions which may contain objects.

### Results
The state of the art results is achieved by ResNeXt101-FPN on the Coco dataset.

### Discussion
The additional mask branch added introduces minor computational addition. The Mask R-CNN is a very promising instance segmentation method and is very flexible and efficient for instance-level segmentation. However, as with the original Faster R-CNN, this architecture struggles with smaller-size objects mainly because of the coarseness of the feature maps.


## General Discussions on Regional Proposal Frameworks:

Deep convolutional neural networks have lifted a lot of the burden for feature engineering which was the main focus in the pre-DCNN era and changed the focus to designing more accurate and efficient network architectures.

Despite the great successes, all methods suffer from the intense labor of creating the bounding boxes. All “newer” methods need exponentially more RAM and GPU in exchange for increased accuracy. Furthermore, the apparent issue of small-size object detection and localization. Using the architectures still need experienced individuals to select appropriate parameters for the task needed.

Several solutions have been suggested by the literature including multi-task learning (Stuffnet) [36], multi-scale representation (IONet) [37] and context modeling (HyperNet) [38]. On the other hand, methods have been proposed to deal with large data imbalances between the objects and the background such as the online mining algorithms (OHEM) [39].



Figure 4. RFCN


One final remark is to highlight the differences between image classification and object detection. An image classifier consists of two modules; the feature extraction module, and the classification module. Such image classifiers are Resnet, VGG, Inception, Dense net, etc. Object detection, on the other hand, is more of architecture with several combinations of modules. The architecture may consist of a feature extraction module, a region proposal network, a regression model, U-Net, etc. The image classification feature extraction is used as part of object detection. The image classification is sometimes referred to as the “backbone network” to the object detection architectures. Object detection is those who have been mentioned in this essay RCNN, Faster-RCNN, etc.


## Future Work:
We briefly used the notions two-step framework which uses region proposal and one step framework which uses the unified framework. I examined some of the regional proposal framework architecture. In general, the two-step approach achieves a better overall accuracy where the unified approach is more for memory-efficiency. Future work of this paper include comparing the unified framework with each other, and its performance with the Region proposal framework.
