# Advance-Traffic-Violation-Detection-System


An AI based system that detects and classifies multiple traffic rule violations from video footage:
- Helmet Violation (No Helmet)
- Triple Riding on Two-Wheelers
- Red Light Crossing

Built using **YOLOv8**, **OpenCV**, **Streamlit**, and **Google Colab**, this system automates the detection process with high accuracy and offers a user-friendly web interface for uploading videos and viewing annotated results.

---

## Problem Statement

Traffic rule violations are a major cause of road accidents, traffic congestion, and law enforcement challenges. Manual detection through traffic personnel or CCTV footage is often inefficient and prone to error. This project aims to **automatically detect multiple types of traffic violations** from video streams using deep learning and computer vision, thereby improving public safety and enforcement accuracy.

---

## Objectives

- Detect multiple types of traffic violations using **YOLOv8** object detection.
- Train custom models for:
  - Helmet vs No-Helmet detection.
  - Triple riding detection.
  - Red light violation tracking.
- Provide annotated output videos highlighting violations.
- Offer a **Streamlit-based web interface** for user interaction.
- Deploy and test using **Google Colab** and **Ngrok** tunneling.

---

## Tech Stack

| Tool            | Purpose                                      |
|-----------------|----------------------------------------------|
| Python          | Core programming language                    |
| OpenCV          | Video processing and annotation              |
| YOLOv8 (Ultralytics) | Real-time object detection               |
| Streamlit       | Frontend web interface for user interaction  |
| Google Colab    | Training and testing environment             |
| Ngrok           | Public access to Streamlit app               |
| NumPy           | Array operations                             |

---

## How It Works

### 1. Helmet Violation Detection
- Trained a YOLOv8 model using labeled images (`helmet` vs `no-helmet`).
- Predicts whether each motorbike rider is wearing a helmet.
- Annotates the video with bounding boxes in:
  - Green → Helmet worn
  - Red → No helmet

### 2. Triple Riding Detection
- Custom dataset with annotations for triple riding on two-wheelers.
- The model detects multiple persons on a single bike and flags if more than two are present.
- Bounding boxes and text alert are drawn on the video.

### 3. Red Light Crossing Detection
- Detects vehicles using YOLOv8.
- Detects red signal using HSV-based color filtering.
- Tracks vehicle motion relative to signal position.
- If vehicle moves across stop line while red light is on → it’s flagged as a violation.

---

## Sample Outputs

### 🔍 Interface (Streamlit)
<img src="outputs/interface01.jpg" width="600"/>
<img src="outputs/inf.jpg" width="600"/>


Interactive frontend where users can upload videos and select the violation type to detect.

---

### Helmet Detection
<img src="outputs/nh.jpg" width="600"/>

Bounding boxes in red or green based on helmet presence.

---

### Triple Riding Detection
<img src="outputs/tr.jpg" width="600"/>

Highlights bikes with three or more persons.

---

### Red Light Crossing
<img src="outputs/rc.jpg" width="600"/>

Marks vehicles violating the signal and shows “Violator” label.

---

## Model Performance

| Violation Type       | Dataset Size | Model Used | Accuracy |
|----------------------|--------------|------------|----------|
| Helmet Detection     | 4000+ images | YOLOv8n    | ~87%     |
| Triple Riding        | 3500+ images | YOLOv8n    | ~89%     |
| Red Light Crossing   | 2500+ images | YOLOv8n + CV | ~87%     |

---


---

## How to Run

### On Google Colab
1. Open the Colab notebook.
2. Mount your Google Drive.
3. Upload trained YOLOv8 weights (`best.pt`) and video files.
4. Run detection cells for each violation type:
   - Helmet → `helmet_detection.py`
   - Triple Riding → `triple_riding.py`
   - Red Light → `red_light.py`
5. Output video is saved and downloadable.

---

### Locally on Your PC

```bash
# 1. Clone the repository
git clone https://github.com/your-username/traffic-violation-detection.git
cd traffic-violation-detection

# 2. Install dependencies
pip install -r requirements.txt

# 3. Start the Streamlit interface
streamlit run app.py


