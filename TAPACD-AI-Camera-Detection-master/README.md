# 🎭 TAPACD — AI Theatre Anti-Piracy Detection System

> AI-based Theatre Anti-Piracy Detection using YOLOv8 and OpenCV

> A real-time AI-powered phone detection system built to prevent unauthorized recording in theatres, classrooms and secure venues.

---

## 🎯 Problem Statement

Unauthorized phone recording in theatres, examination halls and confidential meetings is a growing concern. This system uses computer vision to automatically detect phones, track how long they are held, trigger an alert and log the incident — without any human monitoring required.

---

## 🖼 Demo

![Live Detection](TAPACD.v2i.yolov8/screenshots/Live-Detection.jpg)

> Live camera feed detecting a phone with confidence score 0.68, held for 7 seconds — alert triggered.

---
## 📸 Screenshots

### Live Detection with Bounding Box
![Live Detection](TAPACD.v2i.yolov8/screenshots/Live-Detection.jpg)

### Dim Light Detection
![Dim Light](TAPACD.v2i.yolov8/screenshots/dim.jpg)

### Dark Detection
![Dark](TAPACD.v2i.yolov8/screenshots/dark.jpg)

### Bright Light Detection
![Bright Light](TAPACD.v2i.yolov8/screenshots/bright-light.jpg)


---

## ✨ How It Works

1. **Live camera feed** is captured via webcam at 1280×720
2. **YOLOv8** runs inference on every frame in real time
3. If a phone is detected, a **countdown timer starts**
4. If the phone is held for **7+ seconds**, the system:
   - Triggers a **beep alert** (1500Hz)
   - **Auto-captures** a screenshot with bounding box and confidence
   - **Logs the incident** to a CSV file with date, time and confidence
5. All captured incidents are displayed in the **web dashboard**

---

## 🛠 Tech Stack

| Category         | Technology           |
| ---------------- | -------------------- |
| Object Detection | YOLOv8 (Ultralytics) |
| Web Framework    | Flask                |
| Computer Vision  | OpenCV               |
| Dataset Platform | Roboflow             |
| Language         | Python 3.11          |
| Frontend         | HTML, CSS, Jinja2    |

---

## 📊 Dataset

- **Total Images:** 2,779
- **Annotation Tool:** Roboflow
- **Format:** YOLOv8
- **Classes:** 1 (`phone`)
- **Data Collection:** Photos captured manually in real environments — dim light, bright light, different angles and distances
- **Augmentations applied:**
  - Horizontal flip (50% probability)
  - Random rotation (±10°)
  - Random brightness (±25%)
  - Random exposure (±15%)
  - Gaussian blur (0–1.5px)
  - Salt and pepper noise (1.99%)

> Dataset available on Roboflow Universe:
> [roboflow.com/phone-detection-dov8o/tapacd-gfoft](https://universe.roboflow.com/phone-detection-dov8o/tapacd-gfoft/dataset/2)

---

## 📁 Project Structure

```
yolo_training/
├── TAPACD.v2i.yolov8/
│   ├── train/images/       # Training images
│   ├── valid/images/       # Validation images
│   └── data.yaml           # Dataset config
├── runs/
│   └── detect/train2/
│       └── weights/
│           └── best.pt     # Trained YOLOv8 model weights
├── captures/               # Auto-saved alert screenshots
├── templates/
│   └── index.html          # Web dashboard template
├── app.py                  # Flask application
├── alerts_log.csv          # Incident log with timestamps
└── requirements.txt        # Python dependencies
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install flask ultralytics opencv-python
```

### Run the app

```bash
python app.py
```

Open [http://localhost:5000](http://localhost:5000) in your browser.

> **Note:** Requires a webcam connected to your computer. The trained model weights (`best.pt`) must be present at `runs/detect/train2/weights/best.pt`.

---

## 📋 Alert Log Sample

| Date       | Time     | Confidence | Image                     |
| ---------- | -------- | ---------- | ------------------------- |
| 2026-03-10 | 14:11:14 | 0.76       | ALERT_20260310_141114.jpg |
| 2026-03-10 | 12:29:58 | 0.72       | ALERT_20260310_122958.jpg |
| 2026-01-20 | 10:18:15 | 0.77       | ALERT_20260120_101815.jpg |

> 45+ real incidents logged across multiple testing sessions from November 2025 to March 2026.

---

## 🎯 Real World Use Cases

- 🎭 **Theatres & Cinemas** — prevent piracy recording
- 🏫 **Examination Halls** — detect cheating via phone
- 🏛 **Conference Rooms** — protect confidential presentations
- 🏥 **Hospitals** — enforce no-phone zones

---

## 📈 What I Learned

- End-to-end ML pipeline: data collection → annotation → training → deployment
- Custom dataset creation and augmentation with Roboflow
- YOLOv8 model training and fine-tuning on custom classes
- Real-time video streaming with Flask and OpenCV
- Building a complete web dashboard with incident logging

---

_Dataset collected manually in real environments. Model trained from scratch on custom annotated data._
