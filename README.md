
# 🎭 Video Facial Expression Detection

This project performs **real-time facial expression recognition** from video streams using **OpenCV**, **DeepFace**, and **tf-keras**.
It supports both **webcam input** and **video file processing**, with optional output video generation.

Built to run in **headless environments** (servers, cloud VMs, Docker containers) using `opencv-python-headless`.

---

## 🔧 Features

* Real-time **emotion recognition** using DeepFace
* Support for:

  * Webcam video streams
  * Local video files
* Headless OpenCV backend (no GUI required)
* Bounding boxes and emotion labels drawn directly on frames
* Optional annotated video output (`--output`)
* Progress bars with **tqdm**
* Configurable DeepFace detector backend (OpenCV, RetinaFace, SSD, MTCNN, etc.)
* Works fully offline after model download

---

## 🧠 Detected Emotions

DeepFace returns 7 standard emotion classes:

* **Angry**
* **Disgust**
* **Fear**
* **Happy**
* **Sad**
* **Surprise**
* **Neutral**

These are extracted from DeepFace’s built-in emotion model.

---

## 📦 Installation

Install all required dependencies:

```bash
pip install opencv-python-headless deepface tf-keras tqdm deepface
```

> ✔ No GUI required
> ✔ Compatible with Linux servers and cloud environments

---

## ▶️ Usage

### **1. Run using webcam**

```bash
python detect_expression.py --source webcam
```

### **2. Run on a video file**

```bash
python detect_expression.py --source /path/to/video.mp4
```

### **3. Save annotated output video**

```bash
python detect_expression.py --source input.mp4 --output output_annotated.mp4
```

---

## 🧩 How It Works

1. **Frame Capture**
   Using `cv2.VideoCapture()` (webcam or video).

2. **Face Detection & Emotion Analysis via DeepFace**

```python
analysis = DeepFace.analyze(
    frame,
    actions=["emotion"],
    detector_backend="opencv",
    enforce_detection=False
)
```

3. **Bounding Box Rendering**
   Frame is annotated with:

   * Face bounding box
   * Dominant emotion label
   * Optional confidence scores

4. **Output Handling**

   * Frames are displayed (if GUI is available) or processed headlessly
   * Optional video writer saves the annotated output
   * `tqdm` displays processing progress for video files

---


---

## 🚀 Performance Tips

* Use `detector_backend="opencv"` for the fastest execution
* Reduce frame size for near real-time performance
* GPU acceleration (TensorFlow + CUDA) improves DeepFace speed significantly
* Set `enforce_detection=False` to avoid unnecessary exceptions

---

## 🤝 Contributing

Contributions are welcome!
Feel free to open issues or submit pull requests.

---

## 📜 License

This project is licensed under the **MIT License**.


