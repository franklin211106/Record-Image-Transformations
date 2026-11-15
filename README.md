# Exp-4-Record-Image-Transformations

## Aim:
To write a Python program using OpenCV to perform various geometric transformations on an image.

## Software Used:
Anaconda – Python 3.7  
Jupyter Notebook / VS Code  
OpenCV (cv2)  
NumPy  
Matplotlib  

## Algorithm:

Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the input image in color mode.

Step 3: Image Translation
Create a translation matrix to shift the image
Move the image 50 pixels to the right and 80 pixels down
Apply transformation using cv2.warpAffine()
Display original and translated images

Step 4: Image Scaling

Resize the image to 0.5× (downscale)
Resize the image to 2× (upscale)
Use cv2.resize()
Display original, downscaled, and upscaled images

Step 5: Image Shearing

Create transformation matrices for:
Horizontal shearing
Vertical shearing
Apply transformations using cv2.warpAffine()
Display original and sheared images

Step 6: Image Reflection

Perform flipping using cv2.flip():
Horizontal reflection
Vertical reflection
Both axes
Display all reflected images

Step 7: Image Rotation

Create rotation matrices for:
45° rotation
90° rotation
Use cv2.getRotationMatrix2D() and cv2.warpAffine()
Display original and rotated images

## Program:

### Developed By:
### Name: FRANKLIN F
### Reg.No: 212224240041

```python

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('WhatsApp Image 2026-10-24 at 3.32.56 PM.jpeg')

if image is None:
    raise ValueError("Image not found. Check the file name.")

# Display the original image
plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')
plt.show()

# Step 2: Image Translation
tx, ty = 100, 50

M_translation = np.float32([[1, 0, tx], [0, 1, ty]])

translated_image = cv2.warpAffine(
    image, M_translation, (image.shape[1], image.shape[0])
)

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
plt.title("Translated Image")
plt.axis('off')
plt.show()

# Step 3: Image Scaling
fx, fy = 5.0, 2.0

scaled_image = cv2.resize(
    image, None, fx=fx, fy=fy,
    interpolation=cv2.INTER_LINEAR
)

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
plt.title("Scaled Image")
plt.axis('off')
plt.show()

# Step 4: Image Shearing
shear_matrix = np.float32([
    [1, 0.5, 0],
    [0.5, 1, 0]
])

sheared_image = cv2.warpAffine(
    image, shear_matrix, (image.shape[1], image.shape[0])
)

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))
plt.title("Sheared Image")
plt.axis('off')
plt.show()

# Step 5: Image Reflection
reflected_image = cv2.flip(image, 1)

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
plt.title("Reflected Image")
plt.axis('off')
plt.show()

# Step 6: Image Rotation
(height, width) = image.shape[:2]

angle = 45
center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(center, angle, 1)

rotated_image = cv2.warpAffine(
    image, M_rotation, (width, height)
)

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
plt.title("Rotated Image")
plt.axis('off')
plt.show()

# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150

cropped_image = image[y:y+h, x:x+w]

plt.figure(figsize=(6, 5))
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis('off')
plt.show()


```

## Output:
### Original image:

<img width="360" height="495" alt="image" src="https://github.com/user-attachments/assets/6d3d9100-8bae-408a-9fa1-f9106fc07c60" />


### Image Translation

Original image is displayed

<img width="411" height="517" alt="image" src="https://github.com/user-attachments/assets/542ee49e-7726-453e-bd0d-1df967cef711" />


Translated image (shifted right and down) is displayed

<img width="360" height="495" alt="image" src="https://github.com/user-attachments/assets/6d3d9100-8bae-408a-9fa1-f9106fc07c60" />

### Image Scaling

Original image is displayed

<img width="662" height="362" alt="image" src="https://github.com/user-attachments/assets/61e2e33f-4d14-4b8c-94f7-c9689787c991" />


Downscaled image (0.5×) is displayed
Upscaled image (2×) is displayed



### Image Shearing

Original image is displayed

<img width="411" height="517" alt="image" src="https://github.com/user-attachments/assets/542ee49e-7726-453e-bd0d-1df967cef711" />

Horizontally sheared image is displayed

Vertically sheared image is displayed

<img width="407" height="512" alt="image" src="https://github.com/user-attachments/assets/f080529f-8ca1-4395-bdd5-77f9131b84d8" />



### Image Reflection

Original image is displayed

<img width="402" height="505" alt="image" src="https://github.com/user-attachments/assets/4699d4c1-9f60-470e-b327-083cf82efa69" />


Horizontally flipped image is displayed

Vertically flipped image is displayed

Both-axis flipped image is displayed

### Image Rotation

Original image is displayed

<img width="385" height="498" alt="image" src="https://github.com/user-attachments/assets/9b37ff58-b8df-4003-903e-48eed41417d8" />


45° rotated image is displayed

90° rotated image is displayed

<img width="377" height="512" alt="image" src="https://github.com/user-attachments/assets/41b62fbe-7978-4bb8-9468-2973ee6375a3" />


## Cropped Image:

<img width="640" height="507" alt="image" src="https://github.com/user-attachments/assets/7326d7de-5d2f-4728-9ae8-4ec453854259" />



## Result:

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
