# **Finding Lane Lines on the Road** 

## Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
The project  deliverables are a Jupyter notebook called "P1.ipynb" and a writeup md file called "writeup.md"


### Reflection

### 1. Pipeline Description.

My pipeline consisted of the following steps.
I started out by looping over the test images provided and performed the following transformations:
	a) Created a grayscale of the image
	b) Defined a Kernel size and applied Guassian Smoothing
	c) Defined the parameters for the canny algorithm and applied it on the guassian image in order to detect edges.
	d) Defined a mask using cv2.fillPoly() which creates a four sided polygon, in which lanbe detection will happen.
	e) Defined hough transformation paramters, and then aplied the hough transformation.
	f) Merge the orginial image with the masked lanes from the previous steps.
	g) Print out the images showing the detected lanes.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function in order to
average/extrapolate the line segments you detect to map out the full extent of the lane as a connected straight line
in doing so, I created a new function called "draw_straight_lines" that has the following following steps:
	a) Find the slope of each of the lines "hough lines list input to the new fucntion", if the slope is positive
	that indicates the right lane, if it is negative, that indicates, that this is the left lane.
	b) Average out all the points detected on the left and right lanes.
	c) From the average x and y values of each point calculate the lane line intercept and slope.
	d) Calculate the extended lines and get the moving average.
	e) Plot the lines given the color and thickness as input parameters.


### 2. Identify potential shortcomings with your current pipeline
One potential shortcoming would be what would happen when the lanes are in a new image and fall out the defined verticies.
Another shortcoming could be 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
Improvement in handling curved lines

