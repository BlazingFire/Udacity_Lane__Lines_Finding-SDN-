# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Pipeline Description

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a gaussian blur with canny edge detection to find edges based on gradient difference. Then I created a region of interest by masking and finally applied hough transform to detect left and right lanes in the masked region.

Initially I had applied region of interest masking before doing canny edge detection, this had created an extra pair of edges due to gradient difference between masked and outside region and hence this must be avoided.

In order to draw a single line on the left and right lanes, I the used the lines coordinates found in hough_transform function. From those points i found the average sloped for the points on left and right lane respectively. I also found the topmost point(lowest y coordinate)  on both the lanes Using the average slope and topmost point, I extended the existing lines to meet the image lower horizontal boundary thus creating two single lines on left and right lanes.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when the region of masking is too different for an image as some of the values have been hardcoded based on the assumption that the camera is mounted in the center and the position of car and lane are also almost near the center part of the image. 

Another shortcoming could be the camera perspective as finally a straight line is drawn from topmost y coordinate(hard coded) to bottom of the image which might create some off results.

One more thing is that, current the results dont perform well if there is some curve in the road.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use region masking values as per the image size thus reducing the amount of hardcoding.

Another potential improvement could be to detect only a single left and right lane as in the later examples many lines were detected, probably this could be handles with a better masking of region.
