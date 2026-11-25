# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** Janani S
- **Register No:** 212224230103
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read Image
img = cv2.imread("C:/Users/admin/OneDrive/Documents/Downloads/Image 6 (2).jpg")

# Convert to Grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# 1. Sobel Edge Detection
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.convertScaleAbs(cv2.magnitude(sobel_x, sobel_y))

# 2. Prewitt Edge Detection
prewitt_x = np.array([[-1, 0, 1],
                      [-1, 0, 1],
                      [-1, 0, 1]])

prewitt_y = np.array([[-1, -1, -1],
                      [0, 0, 0],
                      [1, 1, 1]])

px = cv2.filter2D(gray, cv2.CV_32F, prewitt_x)
py = cv2.filter2D(gray, cv2.CV_32F, prewitt_y)
prewitt = cv2.convertScaleAbs(cv2.magnitude(px, py))

# 3. Roberts Edge Detection
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

rx = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
ry = cv2.filter2D(gray, cv2.CV_32F, roberts_y)
roberts = cv2.convertScaleAbs(cv2.magnitude(rx, ry))

# 4. Laplacian Edge Detection
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

# 5. Canny Edge Detection
canny = cv2.Canny(gray, 100, 200)

# Display Results
images = [gray, sobel, prewitt, roberts, laplacian, canny]

titles = ["Original Grayscale",
          "Sobel Edge Detection",
          "Prewitt Edge Detection",
          "Roberts Edge Detection",
          "Laplacian Edge Detection",
          "Canny Edge Detection"]

plt.figure(figsize=(14, 9))

for i in range(6):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()

print("Edge Detection Completed Successfully!")



```

## Output
<img width="780" height="547" alt="image" src="https://github.com/user-attachments/assets/a5476427-10df-47b8-b486-99fa4f62a41d" />



###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
