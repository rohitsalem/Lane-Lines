# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/whiteCarLaneSwitch_gray_scale.png "Grayscale"
[image2]: ./test_images_output/whiteCarLaneSwitch_gaussian.png "Gaussian"
[image3]: ./test_images_output/whiteCarLaneSwitch_canny.png "Canny"
[image4]: ./test_images_output/whiteCarLaneSwitch_roi.png "Region of Interest"
[image5]: ./test_images_output/whiteCarLaneSwitch_hough.png "Hough lines extrapolation"

---

### Reflection
1. The images are first converted into grayscale. 
![alt text][image1]
2. Then the grayscale image is blurred using gaussian technique.
![alt text][image2]
3. Then canny edge detector is run on this gaussian blurred image to find the edges in the image.
![alt text][image3]
4. Running the Canny edge detector finds all the edges in the image, but we are interested in finding just the lanes. so we create a region of interest to just cover the lanes.
![alt text][image4]
5. Then the resulting image is run through a hough line transform and hough lines are found, followed by extrapolating the lines by joining the gaps between the lanes and matching the slopes of the detected lines in draw_lines() function. 
![alt text][image5]

### 2. Identify potential shortcomings with your current pipeline
The pipeline would fail with the challenge video beacause of the curved path and the slopes vary continously, it cannot be the same slope because of the curvature and the extrapolation goes wrong.

### 3. Suggest possible improvements to your pipeline
A possible improvement would be to check on methods to extrapolate curves rather than just using slopes as in case of straight lines and also decreasing the threshold for gaps between the lines to be extraploated, as curves can be treated as small lines joined together. 
