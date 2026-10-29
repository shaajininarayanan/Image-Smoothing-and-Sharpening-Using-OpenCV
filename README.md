# Image Smoothing and Sharpening Using OpenCV

---

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

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

---

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Read the input image using `cv2.imread()`.

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

Apply Laplacian Sharpening using a kernel with `cv2.filter2D()`.

### Step 9:

Convert the image to grayscale and apply the Laplacian Operator using `cv2.Laplacian()`.

### Step 10:

Display each filtered image separately along with the original image for comparison.

---

## Program

### Developed By

- **Name:** Shaajini N
- **Register No:** 212225040395

### Program 1: Image Reading and Display

```python
import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    plt.figure(figsize=(6, 5))
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")
    plt.show()
```

### Program 2: Averaging Filter

```python
import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    averaging = cv2.blur(img, (5, 5))

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(averaging)
    plt.title("Averaging Filter")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 3: Weighted Averaging Filter

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    kernel = np.array([
        [1, 2, 1],
        [2, 4, 2],
        [1, 2, 1]
    ], dtype=np.float32) / 16

    weighted = cv2.filter2D(img, -1, kernel)

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(weighted)
    plt.title("Weighted Averaging Filter")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 4: Gaussian Filter

```python
import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    gaussian = cv2.GaussianBlur(img, (5, 5), 0)

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(gaussian)
    plt.title("Gaussian Filter")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 5: Median Filter

```python
import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    median = cv2.medianBlur(img, 5)

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(median)
    plt.title("Median Filter")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 6: Laplacian Sharpening Using Kernel

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    kernel = np.array([
        [0, -1, 0],
        [-1, 5, -1],
        [0, -1, 0]
    ], dtype=np.float32)

    sharpened = cv2.filter2D(img, -1, kernel)

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(sharpened)
    plt.title("Laplacian Sharpening Using Kernel")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

### Program 7: Laplacian Operator

```python
import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\images\Boy.jpg"
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found. Check the image path.")
else:
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    laplacian = cv2.Laplacian(
        gray, cv2.CV_64F
    )

    laplacian_abs = cv2.convertScaleAbs(laplacian)

    plt.figure(figsize=(10, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(gray, cmap="gray")
    plt.title("Original Grayscale Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(laplacian_abs, cmap="gray")
    plt.title("Laplacian Operator")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

---

## Output

### Original Image

- The input image is read and displayed.

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/6c4cb68e-2697-4fcc-a277-18a86755bcaa" />


### Averaging Filter

- The averaging filter produces a blurred image by averaging neighboring pixels.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b0990636-e9d6-47c4-9b29-e138bdb69351" />


### Weighted Averaging Filter

- The weighted averaging filter smooths the image using a weighted kernel.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/64baa4df-b21c-49c4-b845-06605cca6c34" />


### Gaussian Filter

- The Gaussian filter reduces image noise using Gaussian-weighted smoothing.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5a989514-e15b-469a-88ea-51528130a107" />


### Median Filter

- The median filter reduces impulse noise while preserving edges better than simple averaging in many cases.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e61982bc-05cb-4ee5-a0fd-f94ad49abf60" />

### Laplacian Sharpening Using Kernel

- The sharpening kernel enhances edges and fine details in the image.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/726d96c5-de12-494a-8099-b55a94091fde" />


### Laplacian Operator

- The Laplacian operator highlights regions of rapid intensity change in the grayscale image.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cdbd358f-3ad6-4b9a-8239-058b4cf9981a" />


---

## Result
Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and smooth image details, while sharpening filters enhance edges and fine details for image enhancement and computer vision applications.
Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and smooth image details, while sharpening filters enhance edges and fine details for image enhancement and computer vision applications.
