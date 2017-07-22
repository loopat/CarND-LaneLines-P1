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

Step 1: Copy and converted the image to grayscale 
Step 2: Apply Gaussian smoothing
Step 3: Apply Canny
Step 4: Apply mask
Step 5: Run Hough and draw lines

In order to draw a single line on the left and right lanes, in step 5, I modified the draw_lines() function as the following steps:
(1) Define a class which contains line features
(2) Extract the features into a list named lines_list
(3) Find collineation based on the slope and intercept, and save the lines which meets the condtion (near slope and intercept) into a dictionary named lines_dic
(4) Find the longest lines in left and right, and save them into a dictionary named lines_result
(5) Draw the two lines

#If you'd like to include images to show how the pipeline works, here is how to include an image: 
#![alt text][image1]

### 2. Identify potential shortcomings with your current pipeline

(1) Some of thresholds or region of interest are defined based on adjusting and testing.
    I wonder if it is uesd for detecting more information in the traffic such as cross walk and the lane at the same time, it may bring some confused problems.
    Because some passing cars are also detected horizontal lines.
(2) The dashed line is not very good, especially if the space is too big between two line segments.
(3) There is some deviation in finding the longest lines during drawing lines in step (5).
(4) The lane with large curvature (challenge.mp4) is very bad during the detecting and drawing lines.
(5) Some passing cars, the readside scrub(challenge.mp4) have a great impact on detecting pure lanes lines.

### 3. Suggest possible improvements to your pipeline

(1) Add some other object recognition to ensure where the hough lines comes from.
    It may come from a passing car or some scrub . If we got those information, it might give some clues.
(2）Detect some curves while not just straight lines. It may be very uses for curve.
