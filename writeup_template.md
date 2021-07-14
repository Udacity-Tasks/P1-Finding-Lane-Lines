# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[Gray]: ./example_images/gray_form.png "Grayscale"
[Blur]: ./example_images/blur_form.png "Blur"
[Canny]: ./example_images/canny_form.png "Canny"
[MaskedCanny]: ./example_images/masked_canny_form.png "Masked Canny"
[Hough]: ./example_images/hough_lines.png "Hough Lines"
[Combination]: ./example_images/combination.png "Combination"

---

### Reflection

(### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.)
### 1. Description

My pipeline consisted of 5 steps. 
1) **gray_form:** I converted the images to grayscale
2) **blur_form:** applied gaussian_blur with kernel size 5
3) **canny_form:** made canny transform with lower threshold: 84 and upper_threshold:148
4) **masked_canny:** applied an image mask to keep region of interest by using a polygon
5) **line_form:** drawng hough lines on masked canny transformed image 
6) **lines_edges:** initial image and hough lines were combined with a **weighed_img(img, initial, alpha, beta, gama)** function

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by best fit 1st degree polynomial function for y=mx+b 
To determine the left and right line, slope m was calculated. Therefore, these parameters were used to apply 1st degree polynomial. 

Image Examples:
1) **Gray Form**
 
 ![alt text][Gray]

2) **Blur Form**
 
 ![alt text][Blur]

3) **Canny Form**
 
 ![alt text][Canny]

4) **Masked Canny Form**
 
 ![alt text][MaskedCanny]

5) **Hough Lines**
 
![alt text][Hough]

6) **Combination with initial image**
 
 ![alt text][Combination]
 


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be to increase the degree of the polynomial in the algorithm. By using 1st-degree polynomial, it is possible to draw a straight line. Therefore, in the challenge video, not possible to produce the best fit lines for the road lines with a 1st-degree polynomial. Instead, it is possible to increase the number of the points, then to draw polynomial through these points. 

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use another advanced method to select a region of interest. There is no guarantee to select always correct region, therefore, there should be an algorithm to determine fitting the best RoI in the scene. Also, the selection of the color here is not the best method. More advanced methods should be used. 