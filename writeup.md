# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 4 steps.
1. Convert the images to grayscale. 
2. Apply Canny filter on the images.
3. Cut the images to trapezoids where lane markers likely to be appered.
4. Apply Hough Line Transform to the images.

In order to draw a single line on the left and right lanes, I modified the draw__lines() function by averaging the calcurated lines.
By Hough Transform, we get a lot of short and long lines along the lane markers.
Therefore, by calcurating averaged slope and foot (or maybe intercept is more appropriate), we get a single line on each side.

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming of my program is that drawn lines always fractuate (or vibrate) and sometimes flip to irrevelent places.
This happens usually when a shadow or a structure crossed the road and appeared as an edge.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to smoothe the line by using frame-to-frame information.
While tracking lane markers, it is natural that a line on a lane marker should appear very close to the line in the last frame.
Therefore, we can avoid fractuation of the line by applying time-domain smoothing.