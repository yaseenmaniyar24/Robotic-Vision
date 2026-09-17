# 🤖 Project 1: Image Basics using OpenCV

## 📌 Title

**Image Loading, Saving, Negative Transformation, Brightness and Contrast Adjustment using OpenCV**

---

## 🎯 Aim

To load, display, save, and perform basic image processing operations such as negative transformation, brightness adjustment, and contrast adjustment using Python and OpenCV.

---

## 🧠 Objectives

* To read an image using OpenCV.
* To display an image.
* To save an image in a different format.
* To perform negative image transformation.
* To increase image brightness.
* To increase image contrast.
* To understand basic pixel-level image processing.

---

## 🛠️ Technologies Used

* Python
* OpenCV
* NumPy
* Google Colab

---

## 📚 Theory

### 1. Image Loading

OpenCV provides the `cv2.imread()` function to read an image from a specified file path.

```python
img = cv2.imread("image.jpg")
```

The image is loaded as a NumPy array containing pixel values.

---

### 2. Image Saving

The `cv2.imwrite()` function is used to save an image.

```python
cv2.imwrite("image.png", img)
```

---

### 3. Negative Transformation

Negative transformation inverts the pixel values of an image.

The mathematical expression is:

**s = 255 - r**

where:

* `r` = original pixel value
* `s` = output pixel value

For example:

```text
Original pixel = 50
Negative pixel = 255 - 50 = 205
```

This transformation can be useful for enhancing certain details in an image.

---

### 4. Brightness Adjustment

Brightness can be increased by adding a constant value to the pixel intensities.

In this experiment:

```python
beta = 50
```

A positive value increases brightness.

The OpenCV function used is:

```python
cv2.addWeighted()
```

---

### 5. Contrast Adjustment

Contrast controls the difference between darker and brighter regions of an image.

In this experiment:

```python
alpha = 1.5
```

A value greater than `1` increases contrast.

The OpenCV function used is:

```python
cv2.convertScaleAbs()
```

---

## ⚙️ Algorithm

### Step 1

Import OpenCV and NumPy.

### Step 2

Read the input image using `cv2.imread()`.

### Step 3

Check whether the image was loaded successfully.

### Step 4

Display the original image.

### Step 5

Save the original image.

### Step 6

Apply negative transformation using:

```python
255 - img
```

### Step 7

Increase brightness using a positive `beta` value.

### Step 8

Increase contrast using an `alpha` value greater than 1.

### Step 9

Display and save all processed images.

---

## 💻 Source Code

The complete Python program is available here:

    import cv2
    import numpy as np
    from google.colab.patches import cv2_imshow

    # Load image
    img = cv2.imread('/content/pngtree-artificial-intelligence-robot-on-black-background-rendered-in-3d-x-ray-image_3773982.jpg')

    if img is not None:

    # Display original image
    print("Original Image:")
    cv2_imshow(img)

    # Save original image
    cv2.imwrite('/content/original.png', img)

    # -----------------------------
    # 1. Negative Transformation
    # -----------------------------
    img_negative = 255 - img

    print("Negative Image:")
    cv2_imshow(img_negative)

    cv2.imwrite('/content/negative.png', img_negative)

    # -----------------------------
    # 2. Brightness Adjustment
    # -----------------------------
    beta = 50
    img_brightness = cv2.addWeighted(
        img, 1, np.zeros(img.shape, img.dtype), 0, beta
    )

    print("Brightness Adjusted Image:")
    cv2_imshow(img_brightness)

    cv2.imwrite('/content/brightness.png', img_brightness)

    # -----------------------------
    # 3. Contrast Adjustment
    # -----------------------------
    alpha = 1.5
    img_contrast = cv2.convertScaleAbs(
        img, alpha=alpha, beta=0
    )

    print("Contrast Adjusted Image:")
    cv2_imshow(img_contrast)

    cv2.imwrite('/content/contrast.png', img_contrast)

    print("All images processed and saved successfully.")

    else:
        print("Error loading image. Check the file path.")


## 🖼️ Results

### Original Image
<img width="640" height="359" alt="test image" src="https://github.com/user-attachments/assets/13898b75-5506-4489-97d0-e8ca73d2a152" />


### Negative Image

<img width="640" height="359" alt="Negative " src="https://github.com/user-attachments/assets/f4c9a8e1-a4f5-4ba9-ac50-202939156233" />


### Brightness Adjusted Image

<img width="640" height="359" alt="Brightness " src="https://github.com/user-attachments/assets/6c5c4ac0-d3de-4278-9158-e08b1446153f" />


### Contrast Adjusted Image

<img width="640" height="359" alt="Contrast" src="https://github.com/user-attachments/assets/e0300586-6404-45fd-94cf-f33093406103" />


---

## 📊 Result Analysis

The original image was successfully loaded and displayed using OpenCV.

The negative transformation inverted the pixel intensities of the image. Increasing the brightness made the image lighter, while increasing the contrast enhanced the difference between darker and brighter regions.

---

## 🤖 Robotics Vision Applications

These basic image-processing operations are useful as preprocessing techniques in robotic vision systems.

Applications include:

* Robot object recognition
* Industrial inspection
* Robot navigation
* Feature enhancement
* Image preprocessing
* Machine vision systems
* Object detection

---

## 🎓 Viva / Exam Questions

### Q1. What is OpenCV?

OpenCV is an open-source computer vision library used for image processing, video processing, and computer vision applications.

### Q2. What does `cv2.imread()` do?

It reads an image from a specified file path and returns it as a NumPy array.

### Q3. What does `cv2.imwrite()` do?

It saves an image to a specified file.

### Q4. What is negative transformation?

Negative transformation converts each pixel value using:

```text
s = 255 - r
```

### Q5. What happens when brightness is increased?

The intensity values of pixels are increased, making the image appear brighter.

### Q6. What is contrast?

Contrast represents the difference between the dark and bright regions of an image.

### Q7. What does `alpha` represent?

`alpha` controls the contrast of an image.

### Q8. What does `beta` represent?

`beta` controls the brightness adjustment.

### Q9. Why is NumPy used?

OpenCV images are represented as NumPy arrays, making NumPy useful for numerical and pixel-level operations.

### Q10. Why are image-processing techniques important in robotics?

They help robots extract useful visual information from cameras for tasks such as navigation, object detection, recognition, and inspection.

---

## ✅ Conclusion

The image was successfully loaded, displayed, and saved using OpenCV. Negative transformation, brightness adjustment, and contrast adjustment were also successfully implemented. These techniques provide fundamental image-processing operations that can be used as preprocessing steps in robotic vision systems.
