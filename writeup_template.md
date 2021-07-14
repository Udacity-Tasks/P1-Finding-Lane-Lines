# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./example_images/gray_form.png "Grayscale"

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
 
 ![alt text][image1]

2) **Blur Form**
 
 ![image](https://user-images.githubusercontent.com/35730346/125648880-4db8391d-2e75-4793-ab77-5062f1290360.png)

3) **Canny Form**
 
 ![image](https://user-images.githubusercontent.com/35730346/125648967-d3a9b50e-a03e-4840-bae6-211d76b0afae.png)

4) **Masked Canny Form**
 
 ![image](https://user-images.githubusercontent.com/35730346/125649602-4f7cc2e6-a57c-4cda-9d27-e8103ecbe745.png)

5) **Hough Lines**
 
 ![image](https://user-images.githubusercontent.com/35730346/125649664-e07807c1-7421-48b0-bcdc-1ba2c1aeaa88.png)

6) **Combination with initial image**
 
 ![image](https://user-images.githubusercontent.com/35730346/125649749-270a6a0e-6a88-4ece-b940-210dbce6e7ab.png)
 





### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
