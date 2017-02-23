# **Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

## Reflection

### 1. Pipeline

My pipeline consisted of following steps:
* Convert image to grayscale
![grayscale example](res/0_grayscale.png)
* Apply gaussian blur
![blur example](res/1_blur.png)
* Apply Canny transformation to find edges 
![canny example](res/2_canny_edges.png)
* Clip with polygon mask to only use relevant portion of image
![clip example](res/3_clip_by_polygon.png)
* Find segments using HoughLinesP
![hough lines example](res/4_hough_lines.png)
![hough lines averaged example](res/4_hough_lines_avg.png)
* Draw segments on image
![hough lines averaged example](res/5_overlay.png)
In order to draw a signle lin on left and right lanes, I modified hough_lines function by adding following steps:
* Filter segments with extreme angles and separate tham into two bins (left and right)
* Average left and rigth segments into lines if there are enough segments to represent line

### 2. Identify potential shortcomings with your current pipeline

Car expects to see only two lines, if there are more they will be averaged incorectly.
Sharp turns will result in dissappearing lines.
If camera changes position there will be need in recalibrating.


### 3. Suggest possible improvements to your pipeline

When approximating lines use not only current image, but also results from previous images.
Improve approximation by using not a number of segments, but their total length as threshold.
Filter lines by colour to improve accuracy.
