#**Finding Lane Lines on the Road** 


[//]: # (Image References)

[image2]: ./test_images/processed/processed_solidWhiteCurve.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

* Convert image to grayscale
* Blur image and detect the edge using canny algorithm
* Apply image mask to extract the region of interest
* Hough line transformation
* Draw lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by assuming the region on interest only contains two group of hough lines where one group represents the "left line" of the road, and the other represents the "right line." Base on the assumption, I simplify the process by only consider two set of points from left line and right line respectively. After I extracted out the data points, I did the followings:

1. Calculate the slope and intercept of the left line and right line
2. Calculate the very botton y position for both left line and right line
3. Calculate the two lines intersection

Draw lines based on the above calculation.


Final result on image:

![alt text][image2]



###2. Identify potential shortcomings with your current pipeline

1) The current lane dectection is designed base on the assumption that there's only land lines in the region on interest (no noise), and it is always a straight line. 

2) Light and weather condition has not been considered in the implementation. 

The detection will fail if the car turns or with obstacles in front of the road. It will also fail with insufficient light in the environment and bad weather condition.

###3. Suggest possible improvements to your pipeline

1) Select region of interest more intelligently so that the region only contains the important information we'd like extract.

2) Able to detect curve land lines.

3) Advanced CV Technique to deal with ligh insufficient and bad weather condition.