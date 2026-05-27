# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** Dhanush G
- **Register No:** 2305002006

```python
#expt-4-edge detection-sobel,laplacian,canny
import cv2
import numpy as np

# Load the image
image = cv2.imread('../Desktop/ex01/parrot.jpg')  # Replace with your image path
if image is None:
    raise ValueError("Image not found. Check the file path.")

# Convert to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# ------------------ Sobel Edge Detection ------------------
# Detect edges in X and Y directions
sobelx = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobely = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel_combined = cv2.magnitude(sobelx, sobely)
sobel_combined = cv2.convertScaleAbs(sobel_combined)

# ------------------ Laplacian Edge Detection ------------------
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

# ------------------ Canny Edge Detection ------------------
canny = cv2.Canny(gray, 100, 200)  # Adjust thresholds as needed

# ------------------ Display Results ------------------
cv2.imshow('Original', image)
cv2.imshow('Sobel X', cv2.convertScaleAbs(sobelx))
cv2.imshow('Sobel Y', cv2.convertScaleAbs(sobely))
cv2.imshow('Sobel Combined', sobel_combined)
cv2.imshow('Laplacian', laplacian)
cv2.imshow('Canny', canny)

cv2.waitKey(0)
cv2.destroyAllWindows()

```

##  Output
<img width="293" height="308" alt="image" src="https://github.com/user-attachments/assets/3b89a3f1-f63b-4f17-9faa-b4a0a619cbc4" />
<img width="294" height="308" alt="image" src="https://github.com/user-attachments/assets/5f797646-196e-4c5e-bdd0-46b8ae91180a" />
<img width="292" height="310" alt="image" src="https://github.com/user-attachments/assets/bddbf185-7207-4db7-8d17-9225ec4c703a" />
<img width="294" height="308" alt="image" src="https://github.com/user-attachments/assets/61049d16-8b4b-4f8d-8290-a1ca0fc56142" />
<img width="292" height="308" alt="image" src="https://github.com/user-attachments/assets/1d1319b8-cca2-4f07-a877-fe3beda7dffd" />
<img width="291" height="308" alt="image" src="https://github.com/user-attachments/assets/d15fa958-f8ce-4372-a317-5ee27a7aa47d" />

##  Result
Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
