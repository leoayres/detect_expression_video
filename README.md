
# 🎭 Video Expression Detection

A Python project for **real-time facial expression recognition** using video input.
The system relies on:

* **OpenCV (opencv-python-headless)** for video capture and frame processing
* **DeepFace** for **emotion recognition** and optionally face detection
* **tf-keras** as the deep learning backend
* **tqdm** for progress bars during video processing

Supports both **webcam input** and **video files**, with the option to save annotated output videos.

---

## 🔧 Features

* Real-time **emotion detection** using DeepFace
* Support for webcam or video file input
* Face detection via DeepFace backends (OpenCV, SSD, RetinaFace, MTCNN, etc.)
* Emotion classification: *happy, sad, angry, surprised, fear, neutral, disgust*
* On-frame rendering of bounding boxes and emotion labels
* Optional output video recording
* Works in **headless environments** (Docker, servers, cloud VMs)
* Progress visualization with **tqdm**

---

## 🧠 Emotions Detected (DeepFace Default)

DeepFace recognizes:

* **Angry**
* **Disgust**
* **Fear**
* **Happy**
* **Sad**
* **Surprise**
* **Neutral**

---

## 🚀 Getting Started

### 1. Install Dependencies

```bash
pip install opencv-python-headless deepface tf-keras tqdm
```

If face_recognition is also used:

```bash
pip install face_recognition
```

> *Note:*
> `face_recognition` requires `dlib`, which must be installed with system-specific build tools.

---

## ▶️ Usage

### Run with webcam

```bash
python detect_expression.py --source webcam
```

### Run on a video file

```bash
python detect_expression.py --source path/to/video.mp4
```

### Save annotated output

```bash
python detect_expression.py --source input.mp4 --output output_annotated.mp4
```

---

## 🧩 How It Works

1. **Frame Capture**
   Using `cv2.VideoCapture`.

2. **Face Detection + Emotion Recognition (DeepFace)**

   ```python
   analysis = DeepFace.analyze(frame, actions=["emotion"], detector_backend="opencv")
   ```

3. **Emotion Extraction**

   * DeepFace returns a dictionary with emotion probabilities
   * The dominant emotion is extracted for annotation

4. **Drawing**

   * Bounding box drawn using OpenCV
   * Emotion label overlaid on the frame

5. **Output**

   * Frames displayed or saved to a video file
   * `tqdm` shows processing progress

---


---

## 📈 Notes on Performance

* For faster analysis, set:

  * `detector_backend="opencv"`
  * `enforce_detection=False`
  * Lower video resolution

* Using GPU (TensorFlow + CUDA) significantly speeds up DeepFace.

---

## 🤝 Contributing

Pull requests and improvements are welcome!

---

## 📜 License

This project is licensed under the **MIT License**.

