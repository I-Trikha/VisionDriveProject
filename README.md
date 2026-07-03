# 🚗 VisionDrive: Vision-Based Advanced Driver Assistance System (ADAS)

VisionDrive is a computer vision-based Advanced Driver Assistance System (ADAS) that processes dashcam footage to perform **lane detection**, **vehicle detection**, **vehicle tracking**, **traffic analytics**, and **forward collision warning** in real time.

The project combines classical computer vision techniques with deep learning (YOLOv5) to provide an end-to-end driving assistance pipeline.

---

## Features

- 🚘 Real-time vehicle detection using YOLOv5
- 🛣️ Lane detection using Canny Edge Detection and Hough Transform
- 🚗 Vehicle tracking with unique IDs
- 📊 Live vehicle counting
- ⚠️ Forward collision warning based on vehicle proximity
- 🎥 Annotated output video generation
- 🚦 Region of Interest (ROI) optimization for faster inference

---

## Pipeline

```
Dashcam Video
      │
      ▼
Frame Extraction
      │
      ▼
Road ROI Selection
      │
      ├───────────────┐
      ▼               ▼
Lane Detection    YOLOv5 Vehicle Detection
      │               │
      └──────┬────────┘
             ▼
Vehicle Tracking
             ▼
Collision Risk Estimation
             ▼
Annotated Output Video
```

---

## Demo

### Input
- Front-facing dashcam video

### Output
- Detected lane boundaries
- Detected vehicles
- Vehicle IDs
- Vehicle count
- Collision warning alerts
- Processed video with annotations

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python |
| Deep Learning | PyTorch |
| Object Detection | YOLOv5 |
| Computer Vision | OpenCV |
| Numerical Computing | NumPy |
| Development | Google Colab |

---

## Project Structure

```
VisionDrive/
│
├── notebooks/
│   └── VisionDrive.ipynb
│
├── input/
│   └── Dashcam.mp4
│
├── outputs/
│   └── output_adas.mp4
│
├── images/
│   ├── pipeline.png
│   ├── sample_input.png
│   └── sample_output.png
│
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

## Methodology

### 1. Lane Detection

The lane detection module uses classical computer vision techniques:

- Grayscale conversion
- Gaussian Blur
- Canny Edge Detection
- Region of Interest masking
- Probabilistic Hough Transform
- Lane averaging and smoothing

This approach provides robust lane estimation while maintaining real-time performance.

---

### 2. Vehicle Detection

Vehicles are detected using **YOLOv5 Large (YOLOv5l)**.

The detector identifies common road objects such as:

- Cars
- Trucks
- Buses
- Motorcycles

Only detections above a confidence threshold are retained.

---

### 3. Vehicle Tracking

Instead of using a dedicated tracking algorithm, the project performs lightweight tracking by assigning IDs based on the proximity of object centroids across consecutive frames.

This enables:

- Persistent vehicle IDs
- Vehicle counting
- Motion estimation

---

### 4. Collision Warning

Collision risk is estimated using the apparent size of the detected vehicle's bounding box.

If the bounding box area exceeds a predefined threshold, the system assumes the vehicle is dangerously close and displays a warning.

---

## Results

The generated output video includes:

- Lane boundaries
- Vehicle bounding boxes
- Vehicle IDs
- Total vehicle count
- Collision alerts
- Frame-by-frame road visualization

---

## Installation

Clone the repository

```bash
git clone https://github.com/<username>/VisionDrive.git

cd VisionDrive
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Usage

Open the notebook

```
notebooks/VisionDrive.ipynb
```

Upload a dashcam video when prompted and execute all cells.

The processed video will be generated as:

```
output_adas.mp4
```

---

## Configuration

Some important configurable parameters:

| Parameter | Description |
|------------|-------------|
| YOLO_VARIANT | YOLO model version |
| MIN_CONFIDENCE | Detection confidence threshold |
| LANE_WARNING_THRESHOLD | Lane departure threshold |
| COLLISION_BOX_AREA_THRESHOLD | Collision warning threshold |
| DISPLAY_ZOOM | Visualization scaling |

---

## Future Improvements

- DeepSORT / ByteTrack integration
- Lane curvature estimation
- Distance estimation using monocular depth
- Speed estimation
- Traffic sign detection
- Pedestrian detection
- Driver drowsiness monitoring
- Semantic lane segmentation using deep learning
- Real-time deployment on embedded devices

---

## Tech Stack

- Python
- OpenCV
- PyTorch
- YOLOv5
- NumPy
- Google Colab

---

## Author

**Ishan Trikha**

B.Tech, Mechanical Engineering  
Indian Institute of Technology Kanpur

---

## License

This project is licensed under the MIT License.
