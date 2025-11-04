# EXP 07 : Edge-Linking-using-Hough-Transformm
### NAME : HARI PRIYA M
### REGISTER NO : 212224240047
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program

```python
# DEVELOPED BY
# HARI PRIYA M
# 212224240047

import numpy as np
import cv2
import matplotlib.pyplot as plt

# READ THE COLOR IMAGE (original image)
img_c = cv2.imread("road.jpg")   
img_c = cv2.cvtColor(img_c, cv2.COLOR_BGR2RGB)

# READ THE GRAY IMAGE
gray = cv2.imread("road.jpg", 0)

# Convert BGR to RGB for displaying color image
gray = cv2.GaussianBlur(gray, (3, 3), 0)

# Display original and grayscale image
plt.figure(figsize=(13, 13))
plt.subplot(1, 2, 1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(gray, cmap='gray')
plt.title("Gray Image")
plt.axis("off")
plt.show()

# Apply Canny edge detection
canny = cv2.Canny(gray, 120, 150)

# Show canny edge image
plt.figure(figsize=(6, 6))
plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()

# Detect lines using Hough Transform
lines = cv2.HoughLinesP(canny, 1, np.pi/180, threshold=100, minLineLength=50, maxLineGap=20)

for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(img_c, (x1, y1), (x2, y2), (255, 0, 0), 3)

# Display final result
plt.figure(figsize=(8, 8))
plt.imshow(img_c)
plt.title("Result Image - Hough Line Transform")
plt.axis("off")
plt.show()

```

## Output

### Input image and grayscale image
<img width="1284" height="374" alt="image" src="https://github.com/user-attachments/assets/62319ba6-550d-4ef7-89de-4a205807aeae" />

### Canny Edge detector output
<img width="500" height="374" alt="image" src="https://github.com/user-attachments/assets/d450418a-266e-42cf-b789-c97ff3a50e03" />

### Display the result of Hough transform
<img width="500" height="374" alt="image" src="https://github.com/user-attachments/assets/07898e95-45cf-4570-a82c-4a9765dd472e" />

## Result
Thus, line detection using the Hough Transform was implemented and visualized successfully in Python using OpenCV.
