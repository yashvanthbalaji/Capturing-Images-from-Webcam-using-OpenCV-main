# 🎥 Real-Time Video and Image Processing 🖼️

This project demonstrates foundational **Computer Vision (CV)** operations using Python and the OpenCV library. It captures and processes a live video stream from a webcam, making it an excellent entry point for real-time video manipulation, frame analysis, and image display with Matplotlib.

---

## ✨ Key Features

* **Snapshot Capture**: Capture a single frame from the webcam and save it locally as `captured_frame.jpg`.
* **Live Feed Display**: Display the real-time, high-resolution video stream in a dedicated window.
* **Stream Resizing**: Manipulate the video output by displaying the feed in custom dimensions (e.g., 100×150 pixels).
* **Stream Rotation**: Apply real-time geometric transformations by rotating the live video feed by **90° clockwise**.

---

## ⚙️ Prerequisites

Make sure you have Python installed. Required libraries can be installed using:

```bash
pip install opencv-python matplotlib ipython
```

---

## 🚀 How to Run the Code

The script is divided into three logical steps. It’s recommended to run each section sequentially.

### **Step 1: Capture and Save a Single Frame**

This segment accesses the webcam, captures one image, and saves it.

```python
import cv2

# Initialize webcam
cap = cv2.VideoCapture(0)

# Capture one frame
ret, frame = cap.read()
if ret:
    cv2.imwrite('captured_frame.jpg', frame)

cap.release()
```

---

### **Step 2: Display the Saved Frame**

This segment reads the saved image and displays it using Matplotlib.

```python
import cv2
import matplotlib.pyplot as plt

# Read the saved image
captured_image = cv2.imread('captured_frame.jpg')
captured_image = cv2.cvtColor(captured_image, cv2.COLOR_BGR2RGB)

plt.imshow(captured_image)
plt.title("Captured Frame")
plt.axis('off')
plt.show()
```

---

### **Step 3: Display Live Video**

Choose and run one of the following options. Press **q** to exit the video loop.

#### **Option A: Normal Video Feed**

```python
import cv2

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        break
    cv2.imshow('Normal Video Feed', frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

#### **Option B: Resized Video Feed**

```python
import cv2

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        break
    resized_frame = cv2.resize(frame, (100, 150))
    cv2.imshow('Resized Video Feed', resized_frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

#### **Option C: Rotated Video Feed (90° Clockwise)**

```python
import cv2

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        break
    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    cv2.imshow('Rotated Video Feed', rotated_frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

---

## 💡 Troubleshooting

If you encounter the error **"Error: Could not capture frame"**:

* ✅ **Check Permissions**: Ensure your OS or virtual environment grants access to your camera.
* ✅ **Close Other Apps**: Verify that no other applications (Zoom, OBS, etc.) are currently using the webcam.
* ✅ **Camera Index**: If you have multiple cameras, try changing:

  ```python
  cv2.VideoCapture(0) → cv2.VideoCapture(1)
  ```

---

## 📌 Notes

* Press **q** anytime to exit the video stream.
* Saved snapshots will be stored as `captured_frame.jpg` in your working directory.

---

## 🧑‍💻 Author

Made with ❤️ using **Python + OpenCV**.
