# Staff Tracking System  
### Real-time Multi-Object Tracking, Face Recognition & Seat State Intelligence

View full project at: https://github.com/kimanaru-1010/Nhom-14_BKAS

![Demo picture](./Screenshot%202026-06-29%20at%2014.31.34.png)


A computer vision system that combines **YOLOv8 object detection**, **ByteTrack multi-object tracking**, **InsightFace face recognition**, and **OSNet re-identification** to build an intelligent workspace monitoring system.

The system tracks people and chairs in real time and uses a **Finite State Machine (FSM)** to infer seat occupancy behavior:

> EMPTY → OCCUPIED → AWAY

---

# Project Overview

This project explores real-time **multi-object tracking and identity fusion** for smart environment monitoring such as offices, classrooms, and labs.

It combines:
- Object detection (YOLOv8)
- Multi-object tracking (ByteTrack)
- Face recognition (InsightFace)
- Person re-identification (OSNet)
- Rule-based reasoning (FSM)

---

# System Architecture

### 1. Object Detection
- YOLOv8 detects:
  - People
  - Chairs

### 2. Tracking
- ByteTrack assigns persistent IDs across frames
- Handles motion and occlusion

### 3. Identity Module
- Face recognition: InsightFace
- Re-ID: OSNet + FAISS similarity search
- Identity fusion system merges both signals

### 4. Seat State Machine (FSM)
Each seat has 3 states:

- EMPTY → no person detected  
- OCCUPIED → owner present  
- AWAY → owner temporarily left  

Violation detection triggers when another person occupies a reserved seat.

---

# 📁 Project Structure
```bash
│
├── source/
│ ├── main.py # Full pipeline
│ ├── config.py # Configuration
│ ├── utils.py # Helper functions
│
│ ├── face_wrap.py # InsightFace wrapper
│ ├── reid_wrap.py # OSNet Re-ID module
│ ├── identity.py # Identity fusion logic
│
│ ├── stable_chair.py # Occlusion handling
│ ├── seat_fsm.py # FSM logic
│
│ └── test.py # Lightweight demo
│
├── faces/ # Face dataset
├── yolov8m/ # YOLO model weights
├── video&output/ # Input/output videos
├── test_setting_lib/ # Experiments
├── requirements.txt
└── README.md
```


---

# Installation

## Create environment
```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```

## Install dependencies
```bash
pip install -r requirements.txt
```

---
# Run

## Full system
```bash
cd source
python main.py
```

## Test mode
```bash
python test.py
```

---

# Core Components

## Detection (YOLOv8)

Detects people and chairs in real time.

## Tracking (ByteTrack)

Maintains consistent object IDs across frames.

## Identity System

- Face recognition (InsightFace)
- Re-identification (OSNet)
- FAISS similarity search

## FSM Logic

EMPTY → OCCUPIED → AWAY
          ↓
     violation detection

---

# Key Design Highlights

- Hybrid identity system (Face + ReID)
- Real-time multi-object tracking pipeline
- FSM-based behavioral reasoning system
- Modular architecture for research flexibility
- Occlusion-aware tracking improvements

---

# Limitations
- Requires GPU for real-time performance
- Face recognition sensitive to lighting and occlusion
- YOLO may produce duplicate detections if not tuned
- No deployed web dashboard yet

---

# Future Work
- Web dashboard for real-time monitoring
- REST API integration
- Multi-camera support
- Improved ReID dataset expansion
- Anomaly detection system

---

# Author
- TA Nguyễn Duy Tân (supervisor)
- Nguyễn Trần Đức Hoàng
- Đặng Khánh Linh
- Trần Nguyễn Đức Hưng
