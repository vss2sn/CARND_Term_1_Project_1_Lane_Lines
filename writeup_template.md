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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...:

The idea behind the modification lies in the use of the angles. Since the angles of the lanes will be restricted, the code filters the lines obtained by the hough transform uusing the slopes of the linbes and uses the lowest and heighest possible y value to generate a full line across the image. 

Rather than do this explicitly, it is easier to manipulate the output of the hough transform itself.

Finally, i added in a feature that allows the lines drawn on the previous image to be drawn on the current image in case the current image fails to give good results from the hough filter. Hence by increasing the size of the bins of the hough filter we allow all the edge points of a single dash from a lane to be included as one point. Hence drawing a line over the lane edge uses the average of an entire dash rather than just one edge or the other. This allows for a better sense of direction and correctly identifies the lane rather than pieces (single dash edges) of it that might be skewed. 

#If you'd like to include images to show how the pipeline works, here is how to include an image: 

#![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


1. More tuning required
2. Basic hough filter can be improved with advanced variants. 
3. Changing line fitting to a curve would increase fidelity of a curved road.

### 3. Suggest possible improvements to your pipeline

The above shortcomings could be fixed using the better variants of the hough filter
The lanes on a curved road could be accurately tracked using a poly fit which was a curve, not a line. 
