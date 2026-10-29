# 🎥 Project 2: Basic Video Playback using OpenCV

## 📌 Title

**Video Loading, Frame-by-Frame Reading, Displaying, and Playback using Python and OpenCV**

---

## 🎯 Aim

To load a video file, check whether it opens successfully, read and display the video frame by frame using OpenCV in Google Colab, and release the video resources after processing.

## 🧠 Objectives

1. To understand the basics of video processing using OpenCV.
2. To load a video file using `cv2.VideoCapture()`.
3. To check whether a video file has opened successfully.
4. To read video frames one by one.
5. To display individual video frames using `cv2_imshow()`.
6. To understand the role of frame sequences in video playback.
7. To release video resources after processing.

## 🛠️ Technologies Used

- Python
- OpenCV
- Google Colab
- `google.colab.patches.cv2_imshow`

## 📚 Theory

### 1. Introduction to Video Processing

A video is a sequence of images called **frames** displayed rapidly one after another to create the appearance of motion.

For example, a video recorded at 30 FPS (frames per second) contains approximately 30 frames for every second of playback.

Video processing is an important part of computer vision and robotics because it allows a system to analyze visual information over time.

### 2. Loading a Video

OpenCV provides the `cv2.VideoCapture()` function to open a video file or access a supported camera.

```python
video = cv2.VideoCapture('/content/video_street01.mp4')
```

Here:

- `cv2.VideoCapture()` opens the video file.
- The file path specifies the location of the input video.
- The returned object is used to read frames from the video.

### 3. Checking Whether the Video Opened Successfully

The `video.isOpened()` function checks whether the video capture object was initialized successfully.

```python
if not video.isOpened():
    print("Error: Could not open video.")
```

This check helps identify problems such as an incorrect file path, a missing video file, or an unsupported video format.

### 4. Reading Video Frames

The `video.read()` function reads the next frame from the video.

```python
ret, frame = video.read()
```

It returns two values:

- **`ret`**: A Boolean value indicating whether a frame was successfully read.
- **`frame`**: The image containing the current video frame.

If `ret` is `True`, the frame can be processed or displayed. If it is `False`, the video may have reached its end or a frame could not be read.

### 5. Displaying Video Frames

Google Colab does not support the usual desktop-style `cv2.imshow()` workflow in the same way as a local Python environment. Therefore, this experiment uses `cv2_imshow()`.

```python
cv2_imshow(frame)
```

This function displays the current frame as an image in the Colab output area.

**Note:** `cv2_imshow()` displays frames as separate image outputs. It does not provide smooth, real-time video playback because each displayed frame becomes a separate notebook output.

### 6. Releasing Video Resources

After processing the video, the capture object should be released.

```python
video.release()
cv2.destroyAllWindows()
```

- `video.release()` releases the video capture resource.
- `cv2.destroyAllWindows()` closes OpenCV display windows, if any are open.

Releasing resources is a good programming practice, particularly when working with cameras and repeated video-processing tasks.

## ⚙️ Algorithm

**Step 1:** Import OpenCV and `cv2_imshow`.

**Step 2:** Open the input video using `cv2.VideoCapture()`.

**Step 3:** Check whether the video has opened successfully.

**Step 4:** If the video cannot be opened, display an error message.

**Step 5:** Read the next video frame using `video.read()`.

**Step 6:** Check the returned Boolean value `ret`.

**Step 7:** If a frame is available, display it using `cv2_imshow()`.

**Step 8:** Repeat the reading and displaying process until the video ends or a frame cannot be read.

**Step 9:** Release the video capture object.

**Step 10:** Close any open OpenCV windows.

## 💻 Source Code

The following program is designed to run in **Google Colab**.

```python
import cv2
from google.colab.patches import cv2_imshow

# -----------------------------------
# 1. Load the video
# -----------------------------------
video = cv2.VideoCapture('/content/video_street01.mp4')

# -----------------------------------
# 2. Check if video opened successfully
# -----------------------------------
if not video.isOpened():
    print("Error: Could not open video.")

else:
    print("Video opened successfully.")

    # -----------------------------------
    # 3. Read and display video frames
    # -----------------------------------
    while True:

        # Read the next frame
        ret, frame = video.read()

        # Stop when no frame is available
        if not ret:
            print("End of video reached.")
            break

        # Display the current frame
        cv2_imshow(frame)

# -----------------------------------
# 4. Release video resources
# -----------------------------------
video.release()
cv2.destroyAllWindows()

print("Video processing completed.")
```

### 📝 Code Explanation

| Code | Explanation |
|---|---|
| `import cv2` | Imports the OpenCV library. |
| `cv2.VideoCapture()` | Opens the input video file. |
| `video.isOpened()` | Checks whether the video opened successfully. |
| `video.read()` | Reads the next frame. |
| `ret` | Indicates whether a frame was read successfully. |
| `frame` | Stores the current video image. |
| `cv2_imshow(frame)` | Displays the frame in Google Colab. |
| `break` | Stops the loop when a frame cannot be read. |
| `video.release()` | Releases the video capture resource. |
| `cv2.destroyAllWindows()` | Closes any open OpenCV windows. |

## 🖼️ Input and Output

### Input

Input video file:



https://github.com/user-attachments/assets/33c95743-0d1f-42fb-8f2e-22e846602cc5



The video file must be uploaded to Google Colab or placed at the specified path.

### Output

The program displays the video frames sequentially in the Google Colab notebook.

**Expected output messages:**

```text
Video opened successfully.
End of video reached.
Video processing completed.
```

The actual output depends on the input video and whether it can be opened and read successfully.

### 📸 Results Screenshots

After running the program in Google Colab, capture screenshots of the displayed video frames and add them to this section.

Suggested repository structure:

```text
02_Video_Basics/
│
├── README.md
├── video_street01.mp4
└── results/
    ├── frame_01.png
    ├── frame_02.png
    └── frame_03.png
```

If the video file is large, consider keeping it outside GitHub and documenting a download source or upload instructions instead.

## 📊 Result Analysis

The video file was opened using OpenCV, and its frames were read sequentially using the `video.read()` function. Each successfully read frame was displayed using `cv2_imshow()` in Google Colab.

The program continued reading frames until no further frame was available. Finally, the video capture resource was released.

This experiment demonstrates the basic procedure for reading and processing video data using OpenCV.

## 🤖 Robotics Vision Applications

Frame-by-frame video processing is useful in many robotics applications.

### 1. Robot Navigation

A mobile robot can analyze camera frames to identify paths, obstacles, and landmarks.

### 2. Object Detection and Tracking

Robots can process video frames to detect and follow objects such as people, vehicles, or packages.

### 3. Autonomous Vehicles

Video streams from cameras can help identify road lanes, traffic signs, pedestrians, and nearby vehicles.

### 4. Industrial Inspection

A camera mounted on a robotic arm can inspect products as they move along a production line.

### 5. Surveillance and Monitoring

Robotic systems can analyze video frames to monitor areas and identify relevant visual events.

## 🎓 Viva / Exam Questions

**Q1. What is OpenCV?**

OpenCV is an open-source computer vision library used for image processing, video processing, and computer vision applications.

**Q2. What is a video frame?**

A video frame is an individual image in a video sequence.

**Q3. What is FPS?**

FPS stands for frames per second. It indicates how many frames are displayed or processed per second.

**Q4. What is `cv2.VideoCapture()` used for?**

It is used to open a video file or access a supported camera.

**Q5. What does `video.isOpened()` do?**

It checks whether the video capture object has been initialized successfully.

**Q6. What does `video.read()` return?**

It returns a Boolean value indicating success and the frame that was read.

**Q7. What is the purpose of `ret`?**

The variable `ret` indicates whether the next frame was successfully read.

**Q8. Why is a `while` loop used?**

A `while` loop repeatedly reads and displays frames until the video ends or a frame cannot be read.

**Q9. Why is `cv2_imshow()` used in Google Colab?**

It displays image frames inside a notebook output cell.

**Q10. What is the difference between `cv2.imshow()` and `cv2_imshow()`?**

`cv2.imshow()` is commonly used for displaying images in local desktop applications, while `cv2_imshow()` is a display helper designed for Google Colab.

**Q11. Why is `video.release()` important?**

It releases the video capture resource when it is no longer needed.

**Q12. Can this program provide smooth video playback?**

Not in its current form. `cv2_imshow()` creates separate notebook image outputs. Smooth playback requires a different display approach, such as a local OpenCV window or an HTML video player in a notebook.

**Q13. How is video processing useful in robotics?**

It allows robots to analyze changing visual scenes for navigation, object tracking, obstacle detection, and inspection.

## ✅ Conclusion

The experiment demonstrated how to load a video file, verify that it opened successfully, read individual frames, display them using OpenCV in Google Colab, and release the video resources after processing.

This experiment provides a foundation for more advanced robotic vision applications, including real-time camera processing, object detection, object tracking, and robot navigation.

---

**Repository:** [Robotic-Vision](https://github.com/yaseenmaniyar24/Robotic-Vision)

**Author:** Yaseen

**Domain:** Robotics, Artificial Intelligence, and Computer Vision
