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

1. Convert the image to grayscale, 
<img src="/test_images_output/gray_solidWhiteCurve.jpg" width="480" alt="Grayscale" />

2. Use the gaussian_blur helper function to smooth the grayscale image further and pass it to canny edge helper method. The Canny edge function furthers returns the image with all the edges.
<img src="/test_images_output/edges_solidWhiteCurve.jpg" width="480" alt="Edges" />

3. Now I selected the required region of interest and pass the image through hough transform helper method. This returns me the images with lines detected in the image for given region of interest.
<img src="/test_images_output/lines_solidWhiteCurve.jpg" width="480" alt="Lines" />

4. Finally I pass the hough transformed image having the left and right lane clearly drawn in the weighted_image helper method. This returns the lines superimposed in the original image.
<img src="/test_images_output/final_solidWhiteCurve.jpg" width="480" alt="Final Image" />


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by .

First, I classified the lines as left and right lane. To achieve this classification I use the slope of the lines, for left line the slope are positive while for right lanes the slope are negative. 

Next step was to get the avg slope for left lane lines and right lane lines, alone with the respective centers. 

Using the calculated left and right lane slopes and centers, I calculated the top and bottom points of both left and rifht lane. 

Using the calculated points I finally draw the left and right lane in the image.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 
I found my current solution significantly failing in the challenge vedio. 
Further, this pipeline would not work when there are more line in the vedio frame for example in case of tire marks.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

I can use color detection in my solution pipeline which could further improve the accuracy of the lane detection in the challenge image

Another potential improvement could be to ...

Identify a lane curve that may be there in lane marking.
