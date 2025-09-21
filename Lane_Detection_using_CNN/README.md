# Lane Detection using Canny Edge Detection

## Overview
This repository contains a lane detection pipeline implemented in **Python** using **OpenCV** and **NumPy**.  
The system processes video frames (or images) to identify lane markings on roads, which is a fundamental step in **autonomous vehicles** and **driver assistance systems (ADAS)**.

The pipeline applies classical computer vision techniques:
1. Preprocessing (grayscale + Gaussian blur)
2. Edge detection (Canny)
3. Region of interest masking
4. Line detection (Hough Transform)
5. Lane line averaging and overlay

---

## Project Structure
```

Lane\_Detection\_using\_canny/
│── lane\_detection.py      # Main script with the full pipeline
│── input.mp4              # Sample input video (add your own)
│── canny.mp4              # Saved Canny edges video (output)
│── segment.mp4            # Saved segmented region video (output)
│── hough.mp4              # Saved Hough lines video (output)
│── output.mp4             # Final processed video with lane overlay
└── README.md              # Project documentation

````

---

## Requirements
- Python 3.8+
- OpenCV (cv2)
- NumPy

Install dependencies:
```bash
pip install opencv-python numpy
````

---

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/MONISSRK/Lane_detection_for_autonomous_vehicles.git
   cd Lane_Detection_using_canny
   ```

2. Place your input video in the directory (default: `input.mp4`).

3. Run the script:

   ```bash
   python lane_detection.py
   ```

4. The following outputs will be generated:

   * `canny.mp4` → edges from Canny detection
   * `segment.mp4` → masked region of interest
   * `hough.mp4` → detected Hough lines
   * `output.mp4` → final video with lane overlay

Press **`q`** to stop playback during execution.

---

## Example Pipeline

1. **Canny Edge Detection**
   Extracts strong gradients representing lane edges.

2. **Segmentation (Region of Interest)**
   Applies a triangular mask focusing on the road area.

3. **Hough Line Transform**
   Detects line segments corresponding to lane boundaries.

4. **Final Overlay**
   Draws averaged left/right lane lines on the original frame.

---

## Configuration

Adjust parameters inside `lane_detection.py` to improve results:

| Parameter       | Description                             | Default        |
| --------------- | --------------------------------------- | -------------- |
| `cv2.Canny`     | Edge detection thresholds               | 50, 150        |
| ROI polygon     | Region coordinates for masking          | Fixed triangle |
| `minLineLength` | Minimum line length for Hough transform | 100 px         |
| `maxLineGap`    | Maximum gap between line segments       | 50 px          |

---

## Limitations

* Optimized for **straight lanes** under good lighting conditions.
* Struggles with:

  * Curves
  * Poorly marked or faded lanes
  * Night-time driving or heavy shadows
* Region of interest is **static**; dynamic ROI may be required for robust real-world systems.

---

## Future Improvements

* Dynamic/adaptive ROI
* Curve lane detection using polynomial fitting
* Integration with deep learning for robust lane marking detection
* Real-time performance optimization

---

## License

This project is released under the **MIT License**.
You are free to use, modify, and distribute it with attribution.


