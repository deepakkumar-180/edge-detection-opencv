# EXP-6 Edge-Detection-Opencv

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
# NAME : DEEPAKKUMAR S
# REG NO : 212225230042
# PROGRAM

```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load image
img = cv2.imread("pic1.png")

# Convert to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Sobel operator
sx = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sy = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.convertScaleAbs(cv2.magnitude(sx, sy))

# Prewitt operator
kx = np.array([[-1, 0, 1],
               [-1, 0, 1],
               [-1, 0, 1]])
ky = np.array([[-1, -1, -1],
               [ 0,  0,  0],
               [ 1,  1,  1]])
px = cv2.filter2D(gray, cv2.CV_32F, kx)
py = cv2.filter2D(gray, cv2.CV_32F, ky)
prewitt = cv2.convertScaleAbs(cv2.magnitude(px, py))

# Roberts operator
rx = np.array([[1, 0], [0, -1]])
ry = np.array([[0, 1], [-1, 0]])
gx = cv2.filter2D(gray, cv2.CV_32F, rx)
gy = cv2.filter2D(gray, cv2.CV_32F, ry)
roberts = cv2.convertScaleAbs(cv2.magnitude(gx, gy))

# Laplacian operator
laplacian = cv2.convertScaleAbs(
    cv2.Laplacian(gray, cv2.CV_64F)
)

# Canny edge detector
canny = cv2.Canny(gray, 100, 200)

# Display results
images = [gray, sobel, prewitt, roberts, laplacian, canny]
titles = ["Grayscale", "Sobel", "Prewitt",
          "Roberts", "Laplacian", "Canny"]

plt.figure(figsize=(10, 7))

for i in range(6):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap="gray")
    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()

```
## Output

<img width="1266" height="761" alt="image" src="https://github.com/user-attachments/assets/55383f6e-ef6a-4a7a-afb6-ca6fa81e998d" />


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
