# 2D-Feature-Tracking

## 1. Data Buffer Optimization
In order to track features in an image, two consecutive frames of the scene are required. This can be achieved by creating a buffer of limited size that contains frames. In this case the size is defined to two. At the beginning, the first image is captured and pushed into the buffer. Its features and descriptors are obtained and stored in a data structure. Then, a new frame is captured and is pushed into the buffer. The match process is possible between both frames and we can get the resulting keypoints. This process is repeated the next time we get a new frame. The old frames are erased automatically from the buffer. This is implemented in lines 63 to 74. 

## 2. Keypoint Detection

The keypoint detection functionality enables the user to choose among different keypoint detectors by setting a string variable. This is implemented in the file matching_2D_student.cpp in the function detKeypointsModern. The following keypoint detectors are available to chose:
- HARRIS
- FAST
- BRISK 
- ORB
- AKAZE
- SIFT
 

## 3. Keypoint Removal

Since we only care about the keypoints on the preceding vehicle, a region of interest is defined around the vehicle. The coordinates are.

## 4. Descriptor Extraction

A variety of descriptor extractors are available and are selected by setting the string variable descriptorType in the function descExtract. The following extractors can be selected:

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
We count the keypoints detected for every detector for all ten images. The results are the following:

## 8. Performance Evaluation: Criteria 2
We count the number of keypoints matched for all the possible combinations of detector-extractor. For matching, we use the brute force method and the distance test ratio set to 0.8. The following results show that...

## 9. Performance Evaluatio: Criteria 3
Finally, we log the time it takes for keypoint detection and descriptor extraction.

## Conclusion


