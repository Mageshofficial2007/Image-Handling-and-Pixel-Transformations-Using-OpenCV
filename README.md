# Image-Handling-and-Pixel-Transformations-Using-OpenCV
# NAME : MAGESH BOOPATHI.M
# REG.NO : 212224230145

Step1:
Load an image from your local directory and display it.
```PYTHON
import cv2
import matplotlib.pyplot as plt
```
# Read the image using OpenCV
```python
img = cv2.imread('images.jpg', cv2.IMREAD_COLOR)
```
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
```PYTHON
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
# Display the image using Matplotlib
```PYTHON
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```
Step2:
o Draw a line from the top-left to the bottom-right of the image.

o Draw a circle at the center of the image. 

o Draw a rectangle around a specific region of interest in the image. 

o Add the text "OpenCV Drawing" at the top-left corner of the image.
Draw a line from the top-left to the bottom-right of the image
```PYTHON
# Load the image
image = cv2.imread('images.jpg') 
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```
```PYTHON
import cv2
import matplotlib.pyplot as plt

# Load image
img = cv2.imread("images.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Get image dimensions
h, w = img_rgb.shape[:2]

# First diagonal (top-left to bottom-right)
cv2.line(img_rgb, (0, 0), (w-1, h-1), (255, 0, 0), 2)

# Second diagonal (top-right to bottom-left)
cv2.line(img_rgb, (w-1, 0), (0, h-1), (255, 0, 0), 2)

plt.imshow(img_rgb)
plt.title("Image with Double Diagonal Lines")
plt.axis("off")
plt.show()
```
Draw a circle at the center of the image.
# Load the image
image = cv2.imread('images.jpg')

# Convert BGR to RGB
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

img_rgb.shape

# Replace circle with square
square_img = cv2.rectangle(img_rgb, (200, 30), (500, 330), (255, 0, 0), 10)
# cv2.rectangle(image, top_left, bottom_right, color, thickness)

plt.imshow(square_img)
plt.title("Image with Square")
plt.axis('off')
plt.show()
Draw a rectangle around  the whole image
# Load the image
image = cv2.imread('images.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape
# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (690, 387), (0, 0, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
Add the text "OpenCV Drawing" at the top-left corner of the image.
# Load the image
image = cv2.imread('images.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
Step3:
o Convert the image from RGB to HSV and display it.
    
o Convert the image from RGB to GRAY and display it. 

o Convert the image from RGB to YCrCb and display it. 
    
o Convert the HSV image back to RGB and display it.
# Load the image
image = cv2.imread('images.jpg') 
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
Step4:
o Access and print the value of the pixel at coordinates (100, 100). 

o Modify the color of the pixel at (200, 200) to white.
import cv2
import matplotlib.pyplot as plt

# Read the main image
image = cv2.imread("images.jpg")

# Read the passport-size image
passport = cv2.imread("photo.jpeg")

# Check if images are loaded
if image is None:
    print("Error: images.jpg not found!")
elif passport is None:
    print("Error: photo.jpeg not found!")
else:
    # Size of the inserted image (change these values)
    width = 100
    height = 100

    # Resize the passport image
    passport = cv2.resize(passport, (width, height))

    # Get the size of the main image
    h, w = image.shape[:2]

    # Calculate the center position
    x = (w - width) // 2
    y = (h - height) // 2

    # Paste the passport image at the center
    image[y:y+height, x:x+width] = passport

    # Convert BGR to RGB
    image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    # Display the result
    plt.figure(figsize=(8,6))
    plt.imshow(image_rgb)
    plt.title("Image with Small Photo")
    plt.axis("off")
    plt.show()
Step5:
o Resize the original image to half its size and display it.
# Load the image
image = cv2.imread('images.jpg') 
image.shape
# Resize the image to half its size
resized_image = cv2.resize(image, (690 // 2, 387 // 2))  # (new_width, new_height)
# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
Step6:
o Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.
# Load the image
image = cv2.imread('images.jpg') 
image.shape
# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349
# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
Step7:
o Flip the original image horizontally and display it. 

o Flip the original image vertically and display it.
# Load the image
image = cv2.imread('images.jpg') 
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)
# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)
# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
Step8:
o Save the final modified image to your local directory.



