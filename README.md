# IMAGE-TRANSFORMATIONS


## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import necessary libraries such as OpenCV, NumPy, and Matplotlib for image processing and visualization.

### Step2:

Read the input image using cv2.imread() and store it in a variable for further processing.


### Step3:

Apply various transformations like translation, scaling, shearing, reflection, rotation, and cropping by defining corresponding functions:

1.Translation moves the image along the x or y-axis.
2.Scaling resizes the image by scaling factors.
3.Shearing distorts the image along one axis.
4.Reflection flips the image horizontally or vertically.
5.Rotation rotates the image by a given angle.

### Step4:
Display the transformed images using Matplotlib for visualization. Convert the BGR image to RGB format to ensure proper color representation.

### Step5:
Save or display the final transformed images for analysis and use plt.show() to display them inline in Jupyter or compatible environments.

## Program:
```python
# Developed By: S Sajetha
# Register Number: 212223100049

import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab.patches import cv2_imshow


# ---------- Load & Convert Image ----------
img = cv2.imread('Miles Morales Icon (1).jpg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# ---------- Transformations ----------
def translate(image, x, y):
    M = np.float32([[1, 0, x], [0, 1, y]])
    return cv2.warpAffine(image, M, (image.shape[1], image.shape[0]))

def shear(image, factor):
    rows, cols = image.shape[:2]
    M = np.float32([[1, factor, 0], [0, 1, 0]])
    return cv2.warpAffine(image, M, (cols, rows))

def rotate(image, angle):
    h, w = image.shape[:2]
    center = (w // 2, h // 2)
    M = cv2.getRotationMatrix2D(center, angle, 1)
    return cv2.warpAffine(image, M, (w, h))

# ---------- Apply Transformations ----------
translated = translate(img, 50, 30)
scaled = cv2.resize(img, None, fx=2, fy=2)
sheared = shear(img, 0.3)
reflected = cv2.flip(img, 1)
rotated = rotate(img, 45)
cropped = img[50:200, 50:200]

# ---------- Display All ----------
images = [img, translated, scaled, sheared, reflected, rotated, cropped]
titles = ['Original', 'Translated', 'Scaled', 'Sheared', 'Reflected', 'Rotated', 'Cropped']

plt.figure(figsize=(20, 10))

# Plot 4 on first row, 3 on second
for i in range(len(images)):
    plt.subplot(2, 4, i + 1)
    plt.imshow(images[i])
    plt.title(titles[i], fontsize=12, fontweight='bold')
    plt.axis('off')

plt.tight_layout()
plt.show()

```
## Output:
![image](https://github.com/user-attachments/assets/58c65a0a-bd3b-48ef-9195-c0bbb9840636)


## Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
