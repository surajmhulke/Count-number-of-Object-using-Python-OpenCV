# Count-number-of-Object-using-Python-OpenCV

In this article, we will use image processing to count the number of Objects using OpenCV in Python.

Module needed
OpenCv: OpenCv is an open-source library that is useful for computer vision applications such as image processing, video processing, facial recognition, and detection, etc.
Numpy: Numpy is a python package for scientific computing. It is a popular math library for Machine Learning. The main Object of Numpy is a multidimensional array.
Matplotlib: Matplotlib is a Python library used for data visualization and graphical plotting of the data.
Image Used:.
# Import libraries 
import cv2 
import numpy as np 
import matplotlib.pyplot as plt 

image = cv2.imread('/content/file.enc') 
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) 

blur = cv2.GaussianBlur(gray, (11, 11), 0) 
canny = cv2.Canny(blur, 30, 150, 3) 
dilated = cv2.dilate(canny, (1, 1), iterations=0) 

(cnt, hierarchy) = cv2.findContours( 
	dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE) 
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) 
cv2.drawContours(rgb, cnt, -1, (0, 255, 0), 2) 


print("total object : ", len(cnt)) 

![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/8b07b072-81a1-487c-991a-7b32dfa99331)
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/c4538418-d49c-49a0-b13c-fefba08aa96f)
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/f84127b5-c29e-4f8c-b2e7-5900867b3ef5)
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/17d2edb7-69ca-4ca5-9663-1fe83cf00144)
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/0fbde557-aa5e-4d53-bc3e-f9e88a3758e6)

total object :  163

Stepwise implementation
for coins image 

![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/b1c9fd59-c04a-438a-b5d2-a72371b8ed33)

Step 1: Import required libraries. 

# Import libraries 
import cv2 
import numpy as np 
import matplotlib.pyplot as plt 
Step 2: We will read the image by using “cv2.imread(image-name)” command & then convert this image into grayscale image using “cv2.cvtColor(image-name, cv2.COLOR_BGR2GRAY)” command.


image = cv2.imread('coins.jpg') 
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) 
plt.imshow(gray, cmap='gray') 
 
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/9721e919-386b-4a60-8ba1-c44a6fc75e97)


Step 3: For counting, we have to detect the edges but before detecting the edges we have to make the image blur to avoid the noises. Use “cv2.GaussianBlur(image-name, Kernal size, std. deviation)”. 

blur = cv2.GaussianBlur(gray, (11, 11), 0) 
plt.imshow(blur, cmap='gray') 
 ![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/0cc017a3-17cc-4b78-979e-083b211f1d81)

    



Step 4:  Now we will detect edges using a canny algorithm, 2nd & 3rd parameters in cv2.canny() function are threshold values. a value between 30 & 150 are consider as an edge for this image.

canny = cv2.Canny(blur, 30, 150, 3) 
plt.imshow(canny, cmap='gray') 
 


![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/fd232219-5cf6-4948-88c7-9f1fc61e546b)

Step 5: We can see that edges are not connected. We need to connect the edges, have to make more thiker & visible. 

dilated = cv2.dilate(canny, (1, 1), iterations=0) 
plt.imshow(dilated, cmap='gray') 
 
![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/fb412a46-6684-4ade-a107-5fb090f9aae3)



Step 6: Now we have to calculate the contour in the image & convert the image into RGB from BGR & then draw the contours.

(cnt, hierarchy) = cv2.findContours( 
    dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE) 
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) 
cv2.drawContours(rgb, cnt, -1, (0, 255, 0), 2) 
  
plt.imshow(rgb) 
 

![image](https://github.com/surajmhulke/Count-number-of-Object-using-Python-OpenCV/assets/136318267/7241ac34-2a12-44bd-86cd-b4b9049f71cf)

Step 7: Printing the result

print("coins in the image : ", len(cnt)) 
Output:

coins in the image:  5
Below is the complete implementation:

# Import libraries 
import cv2 
import numpy as np 
import matplotlib.pyplot as plt 
  
image = cv2.imread('coins.jpg') 
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) 
  
blur = cv2.GaussianBlur(gray, (11, 11), 0) 
canny = cv2.Canny(blur, 30, 150, 3) 
dilated = cv2.dilate(canny, (1, 1), iterations=0) 
  
(cnt, hierarchy) = cv2.findContours( 
    dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE) 
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) 
cv2.drawContours(rgb, cnt, -1, (0, 255, 0), 2) 
  
  
print("coins in the image : ", len(cnt)) 
 

coins in the image :  5
