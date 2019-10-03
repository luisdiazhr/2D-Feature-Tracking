# 2D-Feature-Tracking

## 1. Data Buffer Optimization
In order to track features in the preceding vehicle, two consecutive image frames of the scene are required. In this code, we will store these two frames in a buffer of fixed size of two. When the first image is processed, all its data such as keypoints and descriptors are stored in a data structure that is pushed into the buffer. When the second frame arrives, it is pushed to the buffer as well. Once the buffer is full, the keypoint match process between both frames can take place. When a new frame is pushed into the buffer, the oldest frame will be deleted. This is a good way to maintain the memory. This is implemented in lines 63 to 74. 

## 2. Keypoint Detection

This program enables the user to choose among different keypoint detectors by setting a string variable. This is implemented in the file matching_2D_student.cpp in the function detKeypointsModern. The following keypoint detectors are available to choose from:
- HARRIS
- FAST
- BRISK 
- ORB
- AKAZE
- SIFT
 

## 3. Keypoint Removal

A good way to limit the keypoints detection in the preceding vehicle is to draw a bounding box around it. Keypoints outside this region are discarded. The coordinates of the box that enclose the vehicle are cx = 535, cy = 180, w = 180, h = 150. This is implemented like this:

## 4. Descriptor Extraction

A variety of descriptor extractors are available to choose by setting the string variable descriptorType in the function descExtract. The following extractors are available:

- BRIEF
- ORB
- FREAK
- AKAZE
- SIFT

## 5. Descriptor Matching

Matching is implemented in the function "". Two different matching methods can be selected:

- FLANN
- KNN

## 6. Descriptor Filtering
A distance test ratio is used as a way to remove bad pair of keypoint matches. This is implemented in the function knn.

## 7. Performance Evaluation: Criteria 1
To evaluate which keypoint detector is the best, we run all the detectors for all ten images. The results are written into a csv file. The results show the following:

## 8. Performance Evaluation: Criteria 2
A good way to know which detector-extractor is the best one is to count the number of keypoints matched for all the possible combinations. We use the brute force method and the distance test ratio set to 0.8. The results are below:

## 9. Performance Evaluatio: Criteria 3
Another way to know which detector-descriptor combination is the best, is to measure how long the processing time takes. We log the time it takes for keypoint detection and descriptor extraction. The data is written into a csv file. The results are the following:

## Conclusion


