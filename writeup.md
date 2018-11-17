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

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale.
2. Apply gaussian blur with kernel size of 5 to remove noise.
3. Apply canny to detect edges which are lanes in this case.
4. Apply a mask to select only regions of interest, which are more likely to be visible lanes.
5. Apply hough transform to vote on edges that are more likely to be lanes.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. Separate lines into left and right lanes by their slope
2. Apply Least squares polynomial fit on each set of lines to get two 1-degree polynomial functions
2. Draw the above polynomial functions on the image

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![solidYellowCurve.jpg][./test_images_output/solidYellowCurve.jpg]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be it may not detect lanes correctly when there is big curves, since current solution assume the polygon position to be centered in the image/video, also it is detecting straight lines and it would fail on big curves.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to calculate polygon position based on camara position;

Another potential improvement could be to find a better algorithm to detect curves.
