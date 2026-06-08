# 🚨 Suspicious Motion Detection

A real-time motion detection system built with Python and OpenCV that identifies and highlights suspicious movement in surveillance video — designed for security and monitoring use cases.

---

## ✨ Features

- 🔆 **Adaptive light balancing** — uses CLAHE in LAB color space to normalize uneven or poor lighting
- 🎯 **Frame differencing** — detects motion by comparing consecutive frames
- 🔵 **Bilateral filtering** — reduces noise while preserving edges for cleaner detections
- 📐 **Adaptive thresholding** — handles varying lighting conditions across the frame
- 📦 **Contour-based bounding boxes** — filters out small irrelevant movements by minimum area
- 🏷️ **"Suspicious" label** — marks detected motion regions directly on the frame

---

## 🛠️ Requirements

- Python 3.8+
- OpenCV (`opencv-python`)
- NumPy

Install dependencies:

```bash
pip install opencv-python numpy
```

---

## 🚀 Usage

1. Place your video file in the project directory and update the path:

```python
cap = cv2.VideoCapture('robbery.mp4')
```

2. Run the script:

```bash
python motion_detection.py
```

3. A window will display the video with detected motion regions highlighted.
4. Press **`ESC`** to exit.

---

## 🧠 How It Works

| Step | Description |
|------|-------------|
| **Frame resize** | Scales frames to 50% for faster processing |
| **CLAHE balancing** | Equalizes brightness in LAB space to handle lighting inconsistencies |
| **Frame diff** | `cv2.absdiff()` computes pixel-level differences between two consecutive frames |
| **Bilateral filter** | Smooths noise while keeping edges sharp |
| **Adaptive threshold** | Binarizes the diff map using local Gaussian thresholding |
| **Contour filtering** | Ignores contours smaller than 5000px² to eliminate minor noise |
| **Annotation** | Draws green bounding boxes and red "Suspicious" labels on detected regions |

---

## ⚙️ Tunable Parameters

| Parameter | Location | Description |
|-----------|----------|-------------|
| Min contour area | `cv2.contourArea(cnt) < 5000` | Increase to ignore smaller movements |
| Bilateral filter | `bilateralFilter(gray, 15, 9, 9)` | Adjust `d` and sigmas for noise vs. detail tradeoff |
| CLAHE clip limit | `clipLimit=2.0` | Higher = more contrast enhancement |
| Resize factor | `fx=0.5, fy=0.5` | Lower = faster but less accurate |

---

## 📁 Project Structure

```
├── motion_detection.py   # Main script
├── robbery.mp4           # Input video (not included)
└── README.md
```

---

## 📌 Notes

- Frame differencing works best for **static camera** setups. Moving cameras will generate false positives.
- CLAHE preprocessing makes the detector significantly more robust to flickering lights and shadows.
- For outdoor or high-resolution footage, consider increasing the minimum contour area threshold.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
