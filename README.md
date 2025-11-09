# louvre-object-detection

# ART WATCHER – Real-Time Artifact Security System

## 🛡️ Overview

**ART WATCHER** is an intelligent, multi-laptop security solution designed for museums, galleries, and high-value asset facilities. It combines AI-powered object detection, automated movement alerts, audio-triggered recordings, and live monitoring to prevent theft in real-time.

---

## 🚀 Key Features

### 1. Real-Time Artifact Tracking

* **YOLOv8** neural network for object detection, optimized with **OpenVINO**.
* Detects and tracks multiple high-value objects simultaneously.
* Configurable movement thresholds for precise alerts.
* Instant notifications when objects are moved or removed.

### 2. Multi-Laptop Architecture

* **Detection Laptop**: Runs the AI detection engine and triggers alerts.
* **Audio-Triggered Recorder Laptop**: Listens for alert sounds and records video clips automatically.
* **Web Dashboard Laptop**: Displays live object status, movement alerts, and timestamps.

### 3. Automated Evidence Capture

* Video and images captured automatically on theft or movement detection.
* Stored securely with timestamps.
* Preserves chain-of-custody for legal proceedings.

### 4. Live Web Monitoring

* Accessible dashboard showing object status, last seen time, movement history, and connection health.
* Sub-second updates (500ms) for near real-time monitoring.
* Color-coded alerts for immediate situational awareness.

---

## 🏗️ System Architecture

```
┌───────────────┐      ┌──────────────────┐      ┌─────────────────┐
│ Detection Cam │─────▶│ Detection Laptop │─────▶│ Web Dashboard   │
│  (Artifacts)  │      │ (YOLOv8 + OV)    │      │ (Flask + JSON)  │
└───────────────┘      └──────────────────┘      └─────────────────┘
         │
         ▼
┌───────────────────────┐
│ Audio-Triggered Laptop│
│ (Records Video Clips) │
└───────────────────────┘
```

---

## 🛠️ Technical Stack

* **Computer Vision**: OpenCV, YOLOv8, OpenVINO
* **Backend**: Python, Flask
* **Audio Alerts**: Pygame
* **Frontend**: HTML5, CSS3, JavaScript
* **Interprocess Communication**: JSON files

---

## 📦 Installation & Setup

### Prerequisites

```bash
# Python 3.8+
python --version
```

### Setup

```bash
# Clone the repo
git clone <repo-url>
cd art-watcher

# Install dependencies
pip install opencv-python numpy pygame ultralytics openvino flask

# Add alert sound
# Place "AGAIN_fetty.mp3" in the project directory

# Test camera
python -c "import cv2; cap = cv2.VideoCapture(0); print('Camera OK' if cap.isOpened() else 'Camera Error')"
```

---

## 🎮 Usage

### 1. Start Detection Laptop

```bash
python detection.py
```

* Launches YOLOv8 object detection and real-time movement alerts.
* Tracks multiple bottles and plays alert sound on movement.

### 2. Start Web Dashboard Laptop

```bash
python web_server.py
```

* Access dashboard at `http://localhost:5000`
* Displays object presence, last seen, last movement, and connection status.

### 3. Start Audio-Triggered Recorder Laptop

* Listens for alert sound and records clips automatically for evidence.

---

## 🔒 Security Features

* Local network operation – no internet dependency.
* Encrypted and timestamped evidence storage.
* Redundant multi-camera monitoring.
* Instant alerts with <100ms response time.
* Audio-triggered recording ensures evidence even if direct detection is missed.

---

## 📈 Future Enhancements

* Multi-artifact tracking per display case.
* Facial recognition for suspect identification.
* Suspicious behavior prediction.
* Mobile push notifications for alerts.
* Cloud backup of evidence.
* Integration with building access control and thermal imaging.

---

## 👀 Demo Flow

1. Display bottle → Dashboard shows **Object Present** ✅
2. Move bottle → Audio alert triggers + dashboard shows **Movement Detected** 🚨
3. Remove bottle → Dashboard shows **OBJECT MISSING** ⚠️
4. Secondary laptop records video clip automatically.
5. Evidence stored securely with timestamps.

---

*"The best heist is the one that never happens."* – ART WATCHER Team