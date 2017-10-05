[//]: # (Image References)

[image1]: ./output/images/grayscale/solidWhiteCurve.jpg "Grayscale"
[image2]: ./output/images/edges/solidWhiteCurve.jpg "Edges"
[image3]: ./output/images/region/solidWhiteCurve.jpg "Region"
[image4]: ./output/images/weighted/solidWhiteCurve.jpg "weighted"

# Identifying Lane Lines on Driving Input Video using OpenCV
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This code is an example of using [OpenCV](http://opencv.org/) to approximately identify road lane lines from an input video captured 
from the front view of a passenger vehicle driving down a highway. This is the first project as part of the [Udacity Self-Driving Car Engineer Nanodegree](https://www.udacity.com/drive).

# Getting Started

1. [Install Miniconda] (https://conda.io/miniconda.html)
2. Create [environment provided by Udacity in this repository](https://github.com/udacity/CarND-Term1-Starter-Kit)
3. Activate environment on command line with 'source activate carnd-term1' (you can list environments with 'conda env list')
4. Start Jupyter with 'jupyter notebook notebook.ipynb'
5. Browse to URL http://localhost:8888/notebooks/notebook.ipynb
6. Make sure correct kernal is being used by the Jupyter notebook (you'll get an error about 'No such file or directory' for a path such as '/Users/*/anaconda/envs/tensorflow/bin/python') if you don't see the correct kernal listed you have to update conda to list kernals in Jupyter

# Method Architecture

The pipeline method used to determine lane lines has the following architecture:
* Convert to grayscale
* Apply guassian blur
* Extract edges by using canny conversion
* Use only region of interest where lane lines are expected
* Extract Hough lines from converted image

To draw lane lines on the left and right sides I first check to see if the slope is positive or negative then draw the two lines individually.

| Grayscale | Guassian Blur | Edges | Output |
|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
| ![Grayscale example][image1] | ![Guassian blur example][image2] | ![Edges example][image3] | ![Output example][image4] |

# Improvements Needed

* Calculation of lane lines could be smoother between frames by accounting for the previous frame. I could improve this code by having the line drawing function take into account the frame before the current frame. By using information from the previous frame it should be possible to get a smoother line.
* The frame sizes are hard-coded but can be extracted using code. For this exercise I think it's reasonable to assume the frame size but in production
code it would be better to extract and verify the frame size.
* The code currently is filtering out light colors but I could get more precise by specificying specific line colors like yellow.