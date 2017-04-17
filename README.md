# **Finding Lane Lines on the Road** 


[//]: # (Image References)

[image2]: ./test_images/processed/processed_solidWhiteCurve.jpg "Grayscale"

---

### Pipeline
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



### Potential shortcomings with the current pipeline

1) The current lane dectection is designed base on the assumption that there's only two land lines in the region on interest (no noise), and it is always a straight line. 

2) Light and weather condition has not been considered in the implementation. 

3) If there's other stright line showing the region on interest, e.g. car showdow, then the pipeline might detect it as a landline.

The detection will fail if the car turns or with other "non-landline" strait lines. It will also fail with insufficient light in the environment and bad weather condition.

### Future improvements 

1) Select region of interest more intelligently so that the region only contains the information we'd like extract. 

2) Use better compute vision algorithm to detect the curve land lines. E.g., The Hough method for Curve detection. http://homepages.inf.ed.ac.uk/rbf/BOOKS/BANDB/LIB/bandb4_3.pdf

3) Advanced CV Technique to deal with ligh insufficient and bad weather condition.