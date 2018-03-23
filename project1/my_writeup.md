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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a Gaussian blur with kernel size of 5. Next, I used canny edge detection with low_threshold = 50 and high_threshold = 150. Then I defined a four sided polygon to mask. After run Hough on edge detected image, I get the output line as an array containing endpoints of detected line segments.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first calculating the slope of left and right lanes. Then I divide them to two groups(left and right lanes) and get the intercept through x1, x2, y1, y2 on lanes. Finally, I substitute the slope and intercept I get into points that is determined to be on the start and end of the lane. Do this step to both left and right lanes in order to draw the whole thick red lanes.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when detecting in video sometimes there are noises slope on detecting so that those red slopes we don't want may appear accidentally.

Another shortcoming could be that when I applied pipeline to optional challenge video, it is difficult to distinguish left and right lanes from contours of roadside and landscope like trees. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to test and improve those parameters I chose. The noise in detection result may be eliminated.

Another potential improvement could be to improve the draw_lines() function. Since I just substituted the slope and intercept I got into determined points, it is better to get those points automatically according to images. And also maybe we can use algorithms like kmeans with k = 2 to get the slope instead of two invariable ranges.
