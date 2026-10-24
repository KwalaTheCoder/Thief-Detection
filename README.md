# Suspicious Motion Detection

An educational OpenCV notebook for highlighting motion regions in fixed-camera surveillance footage using frame differencing and contour analysis.

## Pipeline

- CLAHE-based lighting normalization
- Bilateral noise reduction
- Consecutive-frame differencing
- Adaptive thresholding
- Contour filtering and bounding-box annotation

## Run

```bash
pip install jupyter opencv-python numpy
jupyter notebook Thief_Detection.ipynb
```

Set the video path and tune the minimum contour area for the camera resolution and environment.

## Important limitation

The system detects visual motion; it does not determine intent or identify theft. Use neutral interpretations, respect privacy and applicable law, and keep a human reviewer in the loop.
