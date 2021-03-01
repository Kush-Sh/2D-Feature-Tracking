# 2D Feature Tracking

<img src="images/keypoints.png" width="820" height="248" />

In this project with the help of mono camera, we are tracking a particular object in our environment with the help reliable tracking of the features in succussive images. So, we can calculate the time to collision TTC with vehicle in front of self-driving car. We are using OpenCV cross-platform library, using which we can develop real-time computer vision applications. It mainly focuses on image processing object detection.

Particular steps are followed to achieve the goal –
1. Continuous images are taken from the camera as the autonomous vehicle moves, saving all the images in the hardware will eventually run out of space and slows the process speed. To over come is this, we are aiming our system to save on only few consecutive images (2 or 3 images at the time of process). With the help of RING BUFFER, we are pushing one image form one side and removing from the other side maintaining the Data buffer size, which is in this case is 2.

2.	Now the buffer is ready with selectable images, Feature Extraction or identifying good features will be perform on it. We experimented with a few of the known feature extractors, namely HARRIS, FAST, BRISK, ORB, AKAZE, and SIFT feature extractor. The OpenCV library is one of the best libraries available and as processing speed is key for computer vision, we are using the featured detection function which are already mentioned in OpenCV.
With the help of if else one of the feature detection technique will be selected.

3. Now as we are able to calculate the key points in sets of images with the help of OpenCV different algorithms. We bound our focus only on preceding vehicle, to whom we in future calculate the TTC. To do this, we are going to define the rectangle only use the key points within the rectangle for further processing.

4. Descriptors: they are the way to compare the key points. They summarize, in vector format (of constant length) some characteristics about the key points. For example, it could be their intensity in the direction of their most pronounced orientation. It's assigning a numerical description to the area of the image the key point refers to.
Some important things for descriptors are:
•	they should be independent of key point position.
•	they should be robust against image transformation.
•	they should be scale independent.
Same as feature detection, we experimented with a few of the known Key point Descriptors, namely BRIEF, ORB, FREAK, AKAZE and SIFT and make them selectable by setting a   string accordingly.

5. Last step two steps are descriptor matching. In this second last step we approach to image matching consists of detecting a set of interest points each associated with image descriptors from image data. Once the features and their descriptors have been extracted from two or more images, the next step is to establish some preliminary feature matches between these images. Two main algorithm of matching are –
•	Brute-Force Matcher
•	FLANN(Fast Library for Approximate Nearest Neighbors) Matcher
 
6. Last step is to use the K-Nearest-Neighbor (with k Neighbor = 2) matching to implement the descriptor distance ratio 0.8, which looks at the ratio of best vs. second-best match to decide whether to keep an associated pair of keypoints.

<img src="images/Matching keypoints low resolution.jpg" width="820" height="248" />


## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.
