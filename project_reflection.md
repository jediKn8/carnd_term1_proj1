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

1. To convert the images to grayscale, 
[image2]: ./test_images_output/gray_solidWhiteCurve.jpg "Grayscale"

<img src="/test_images_output/gray_solidWhiteCurve.jpg" width="480" alt="Grayscale" />

2. Use the gaussian blur helper function to smooth the grayscale image further and pass it to canny edge helper method.
which returns the image with all the edges

[image3]: ./test_images_output/edges_solidWhiteCurve.jpg "Edges"
<img src="/test_images_output/edges_solidWhiteCurve.jpg" width="480" alt="Edges" />

3. Now I selected the required region of interest and passed the image through hough transform helper method.

[image4]: ./test_images_output/lines_solidWhiteCurve.jpg "Lines"
<img src="/test_images_output/lines_solidWhiteCurve.jpg" width="480" alt="Lines" />

4. Finally I use the weightes image which is my final output. which is basically the superimposing of the hough transform lines in my original image.
[image5]: ./test_images_output/final_solidWhiteCurve.jpg "Final Image"
<img src="/test_images_output/final_solidWhiteCurve.jpg" width="480" alt="Final Image" />


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by .

I first divided the lines among the left lanes and right lanes. Along with the lanes I captured the left lane slope and right lane slope as well as left and right centers. This was further fed into a function to get the points for my line. These points were further used to get the final left and right projections in the image.



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 
I am not using color detection in my pipeline which chould further improve the accuracy of the lane detection

Further, my pipeline would not work when the there is no lane lines. even more if there is any additional line along the lane edge, the pipeline would not be able to get the required result.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Accurately identify the color of the lane lines.

Another potential improvement could be to ...

To be able to identify the lane when there is no lane line in the road.
