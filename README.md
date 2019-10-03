# 2D-Feature-Tracking

## 1. Data Buffer Optimization
In order to track features in the preceding vehicle, two consecutive image frames of the scene are required. In this code, we will store these two frames in a buffer of fixed size of two. When the first image is processed, all its data such as keypoints and descriptors are stored in a data structure that is pushed into the buffer. When the second frame arrives, it is pushed to the buffer as well. Once the buffer is full, the keypoint match process between both frames can take place. When a new frame is pushed into the buffer, the oldest frame will be deleted. This is a good way to maintain the memory. 

*This is implemented in lines 63 to 74 in MidTermProject_Camera_Studet.cpp* 

## 2. Keypoint Detection

This program enables the user to choose among different keypoint detectors by setting the string variable detectorType. The following keypoint detectors are available to choose from:
- HARRIS
- FAST
- BRISK 
- ORB
- AKAZE
- SIFT
 
 *This is implemented in lines 103 to 113 in MidTermProject_Camera_Student.cpp*

## 3. Keypoint Removal

A good way to limit the keypoints detection in the preceding vehicle is to draw a bounding box around it. Keypoints outside this region are discarded. The coordinates of the box that enclose the vehicle are cx = 535, cy = 180, w = 180, h = 150. 

*This is implemented in line 119 in MidTermProject_Camera_Student.cpp*

## 4. Descriptor Extraction

A variety of descriptor extractors are available to choose by setting the string variable descriptorType. The following extractors are available:

- BRIEF
- ORB
- FREAK
- AKAZE
- SIFT

*This is implemented in line 174 in MidTermProject_Camera_Student.cpp*
## 5. Descriptor Matching

The function matchDescriptors in matching2D_Student.cpp uses FLANN or KNN to match descriptors. 

*This is implemented in line 196 in MidTermProject_Camera_Student.cpp*

## 6. Descriptor Filtering
A distance test ratio is used as a way to remove bad pair of keypoint matches. This is implemented inside the function matchDescriptors in matching2D_Student.cpp.

## 7. Performance Evaluation: Criteria 1
To evaluate which keypoint detector is the best, we run all the detectors for all ten images and we compare how many keypoints are detected in each one. The results are stored in the file *build/Performance_1.csv*.

## 8. Performance Evaluation: Criteria 2
A good way to know which detector-extractor is the best one is to count the number of keypoints matched for all the possible combinations. We use the brute force method and the distance test ratio set to 0.8. The results are stored in the file *build/Performance_2.csv*.

## 9. Performance Evaluatio: Criteria 3
Another way to know which detector-descriptor combination is the best, is to measure how long the processing time takes. We log the time it takes for keypoint detection and descriptor extraction. The data is written into a csv file. The results are stored in the file *build/Performance_2.csv*.

## Conclusion

According to the data in Performance_2.csv the three fastest combinations of detector-descriptor are:

- FAST-BRIEF
- FAST-BRISK
- FAST-ORB


