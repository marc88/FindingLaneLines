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

1) Convert given image to grayscale
2) Apply gaussian blur to smoothen the image.
3) Use Canny Edge Detection to detect high gradient changes or edges
4) Define an area where lines are to be found. This is achieved by blacking out unwanted areas of the image.
5) Use Hough transform detection to find the lines (intersections in hough space) in the region of interest of the image. Modify draw lines function to extrapolate lanes.
6) Superimpose the found lines on the initial image to view the final output.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by;
1) Increase thickness (minor)
2) iterate over every line returned by hough transform detection by calculating the changing slope given the x-coordinate changes.Then, we take the euclidean measure to calculate the longest lines on each such iteration.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]

[image1]: ./output_images/solidYellowCurve2.jpg


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lanes are curved. We're relying on straight lines.

Another shortcoming could be the failure on high quality video examples. The pipeline still fails for the challenge video and the lane lines are all over the place.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to detect curved lanes and make it work on challenge video

Another potential improvement could be to deal with videos at night and if the roads are broken such that lane lines are not regular.
