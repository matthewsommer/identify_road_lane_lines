[//]: # (Image References)

[image1]: ./test_images_output/grayscale/solidWhiteCurve.jpg "Grayscale"
[image2]: ./test_images_output/edges/solidWhiteCurve.jpg "Edges"
[image3]: ./test_images_output/region/solidWhiteCurve.jpg "Region"
[image4]: ./test_images_output/weighted/solidWhiteCurve.jpg "weighted"

# Identifying Lane Lines on Driving Input Video using OpenCV
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This code is an example of using [OpenCV](http://opencv.org/) to approximately identify road lane lines from an input video captured 
from the front view of a passenger vehicle driving down a highway. This is the first project as part of the [Udacity Self-Driving Car Engineer Nanodegree](https://www.udacity.com/drive).

# Key Tech

* Python
* Jupyter (Only used to execute the code for this project)
* OpenCV

### Pipeline Methods

* Convert to grayscale
* Apply guassian blur
* Extract edges by using canny conversion
* Use only region of interest where lane lines are expected to be
* Extract Hough lines from converted image

To draw lane lines on the left and right sides I first check to see if the slope is positive or negative then draw the two lines individually.

| Grayscale | Guassian Blur | Edges | Output |
|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
| ![Grayscale example][image1] | ![Guassian blur example][image2] | ![Edges example][image3] | ![Output example][image4] |

### Shortcomings with Current Pipeline

My current code doesn't work with the optional challenge which requires fitting a higher order polynominal to the lane lines.

I think my calculation for the lane lines could be smoother between frames.

The frame sizes are hard-coded but can be extract using code. For this exercise I think it's reasonable to assume the frame size but in production
code it would be better to extract and verify the frame size.

### Possible Improvements to Pipeline

I could improve this code by having the line drawing function take into account the frame before the current frame. By using information
from the previous frame it should be possible to get a smoother line.

The code currently is filtering out light colors but I could get more precise by specificying specific line colors like yellow.
