# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [SAMRITHA R]  
- **Register Number:** [212224040286]

  ### Ex. No. 01
```.PY
import cv2
import matplotlib.pyplot as plt

print("EXPERIMENT 1: IMAGE HANDLING AND PIXEL TRANSFORMATION USING OPENCV")
print("NAME: SAMRITHA R")
print("REGISTER NUMBER: 212224040286")

img = cv2.imread('sampic.jpeg', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError("Please keep sampic.jpeg in the same folder as this notebook.")

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()

height, width = img.shape[:2]
print("Image Shape:", img.shape)

line_img = img_rgb.copy()
cv2.line(line_img, (0, 0), (width - 1, height - 1), (255, 0, 0), 2)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()

circle_img = img_rgb.copy()
cv2.circle(circle_img, (width // 2, height // 2), min(width, height) // 4, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()

rectangle_img = img_rgb.copy()
cv2.rectangle(rectangle_img, (0, 0), (width - 1, height - 1), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()

text_img = img_rgb.copy()
cv2.putText(text_img, "SAMRITHA R", (30, min(100, height - 10)),
            cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 255), 3)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()

image_rgb = img_rgb.copy()

image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis('off')
plt.show()

image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis('off')
plt.show()

image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis('off')
plt.show()

image = img.copy()

print("Pixel value at (100, 100):", image[100, 100])

image[200:min(500, height), 200:min(500, width)] = [255, 255, 255]

image_rgb_modified = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb_modified)
plt.title("Image with White Block")
plt.axis('off')
plt.show()

resized_image = cv2.resize(image, (width // 2, height // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print("Resized Image Shape:", resized_image.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis('off')
plt.show()

roi = img[50:min(150, height), 50:min(150, width)]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis('off')
plt.show()

flipped_horizontally = cv2.flip(img, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis('off')
plt.show()

flipped_vertically = cv2.flip(img, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis('off')
plt.show()

final_image = img.copy()
cv2.line(final_image, (0, 0), (width - 1, height - 1), (255, 0, 0), 2)
cv2.circle(final_image, (width // 2, height // 2), min(width, height) // 4, (0, 255, 0), 5)
cv2.rectangle(final_image, (0, 0), (width - 1, height - 1), (0, 0, 255), 5)
cv2.putText(final_image, "POOJA SRI P", (30, min(100, height - 10)),
            cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 255), 3)

cv2.imwrite('final_modified_image.jpeg', final_image)

print("Final modified image saved successfully as final_modified_image.jpeg")
```

## Output:
<img width="407" height="532" alt="image" src="https://github.com/user-attachments/assets/20e036f4-5d0d-49b9-aebd-54e2cfe94b19" />
<img width="393" height="507" alt="image" src="https://github.com/user-attachments/assets/08bad338-b439-4a96-87bc-9c683403bf28" />
<img width="400" height="522" alt="image" src="https://github.com/user-attachments/assets/069088a9-47a0-4454-b4b1-f077c84620f7" />
<img width="391" height="507" alt="image" src="https://github.com/user-attachments/assets/c5a2c43e-cec5-4852-810a-54e4c43cc6a1" />
<img width="372" height="510" alt="image" src="https://github.com/user-attachments/assets/e68dfca0-212c-4b8e-b2c4-0128ed3112c9" />
<img width="382" height="513" alt="image" src="https://github.com/user-attachments/assets/1d074a2f-b542-4109-912b-5cbb3966c56b" />
<img width="407" height="510" alt="image" src="https://github.com/user-attachments/assets/78792716-aa4a-41f0-b5d1-3a0529612993" />
<img width="391" height="512" alt="image" src="https://github.com/user-attachments/assets/26e8aa94-27ae-4233-b6b2-d16c0ac4a46b" />
<img width="417" height="523" alt="image" src="https://github.com/user-attachments/assets/2639667b-c87d-491a-9fe9-e14a95918588" />
<img width="387" height="506" alt="image" src="https://github.com/user-attachments/assets/112a59db-8755-4d84-9031-5b4457600f9d" />
<img width="382" height="510" alt="image" src="https://github.com/user-attachments/assets/878358e2-eff4-4385-a07a-2eb24188986c" />
<img width="626" height="520" alt="image" src="https://github.com/user-attachments/assets/2fa12a70-fb6e-4b75-a129-286c75c38a25" />
<img width="492" height="397" alt="image" src="https://github.com/user-attachments/assets/9bc4076b-f7c2-4e67-8909-80e3719414f4" />
<img width="382" height="512" alt="image" src="https://github.com/user-attachments/assets/22ad9ccb-8be0-4425-8cf0-a01f9a1f5a19" />
<img width="397" height="511" alt="image" src="https://github.com/user-attachments/assets/cc6d1d50-00fc-4174-af44-d270cae2d83a" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

