# Self-Driving-Car-Term1 project1 lane line detection
The goal of this project is to detect the lane lines in an image or video. The key steps Canny edge detection and Hough transform to find lines from the edge image 
1.	Main Pipeline:
step1: grayscale the image then apply Gaussian blur
step2: canny edge detection
step3: apply a ployfilled mask
step4: Hough transform w/ line extrapolation method*
step5: combine the extrapolated lines with the original image using cv2.addWeighted function
*Line extrapolation method:
	First slope is calculated on the lines from Hough transform
		line_slope = (y2-y1)/(x2-x1)
Next, left and right slope is recognized by checking the sign of each line’s slope: positive slope is right line, negative slope is left.
Next, both left and right line slope are averaged using their Median value (slightly better than mean due to outliers)
Next average the x and y vertices for both left and right lines to get the middle point for both left and right line
Last the top and bottom vertices for both the left and right line can be calculated using their average slope and middle point
