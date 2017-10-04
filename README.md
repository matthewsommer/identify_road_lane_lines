# Identifying Lane Lines on Driving Input Video using OpenCV

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/grayscale/solidWhiteCurve.jpg "Grayscale"
[image2]: ./test_images_output/edges/solidWhiteCurve.jpg "Edges"
[image3]: ./test_images_output/region/solidWhiteCurve.jpg "Region"
[image4]: ./test_images_output/weighted/solidWhiteCurve.jpg "weighted"

---

### Pipeline 

* Convert to grayscale
* Apply guassian blur
* Extract edges by using canny conversion
* Use only region of interest where lane lines are expected to be
* Extract Hough lines from converted image

To draw lane lines on the left and right sides I first check to see if the slope is positive or negative then draw the two lines individually.

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]

### Shortcomings with your current pipeline

My current code doesn't work with the optional challenge which requires fitting a higher order polynominal to the lane lines.

I think my calculation for the lane lines could be smoother between frames.

The frame sizes are hard-coded but can be extract using code. For this exercise I think it's reasonable to assume the frame size but in production
code it would be better to extract and verify the frame size.

### Possible improvements to your pipeline

I could improve this code by having the line drawing function take into account the frame before the current frame. By using information
from the previous frame it should be possible to get a smoother line.

The code currently is filtering out light colors but I could get more precise by specificying specific line colors like yellow.
