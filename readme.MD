# Day 1 Returnables

This notebook demonstrates a **Dynamic Time Warping (DTW)**-based alignment and comparison between two time-series sequences extracted from videos of the **same moment**.

---

## Files Included

- **Notebooks/Day 1.ipynb**  
  Contains all the code and visualizations for:
  - Extracting time-series from video frames
  - Calculating DTW alignment

---

## Objective

To analyze and verify whether two videos of the *same moment* yield similar motion patterns or frame dynamics using DTW.  
Visual outputs help validate the similarity qualitatively.

---
## Results
```
[INFO] Processing video: video1.mp4
[INFO] FPS: 30.07, Total Frames: 435, Duration: 14.47s
[INFO] Keypoints saved to ../data\video1_keypoints.csv
[INFO] Frames processed: 434
[INFO] Time range: 0.00s to 14.40s


[INFO] Processing video: video2.mp4
[INFO] FPS: 30.00, Total Frames: 1431, Duration: 47.70s
[INFO] Keypoints saved to ../data\video2_keypoints.csv
[INFO] Frames processed: 301
[INFO] Time range: 21.00s to 31.00s

[INFO] Preprocessing keypoints...
DTW Distance Score: 140.83
```
Only running the important part of videos 1 and videos 2
---

## Setup (Optional)

If you'd like to run the notebook:

```bash
python -m venv venv
source venv/bin/activate   # or venv\\Scripts\\activate on Windows
pip install -r requirements.txt
