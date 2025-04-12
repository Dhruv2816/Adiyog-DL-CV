# Day 1 Returnables

This notebook demonstrates a **Dynamic Time Warping (DTW)**-based alignment and comparison between two time-series sequences extracted from videos of the **same moment**.

---

## Files Included

- **Notebooks/Day 1.ipynb**  
  Contains all the code and visualizations for:
  - Extracting keypoints from video frames using MediaPipe Pose Detection
  - Calculating DTW alignment (including preprocessing, resampling, and DTW computation)
  - Saving debug frames with keypoints drawn for verification
- **Data/video1_keypoints.csv**
- **Data/video2_keypoints.csv**

---

## Objective

To analyze and verify whether two videos capturing the *same moment* yield similar motion patterns or frame dynamics using DTW.  
Visual outputs help validate the similarity qualitatively and are used to understand where variations may occur.

---

## Results

- **Keypoint Extraction:**  
  Videos were processed to extract pose keypoints and saved as CSV files.
  
- **Time Windowing:**  
  Video 1 was processed entirely (0.00s to 14.40s), while Video 2 was trimmed to the segment from 21.00s to 31.00s.

- **Preprocessing:**  
  Only major (left-side) joints were selected (indices `[11, 13, 15, 23, 25, 27]` corresponding to the left shoulder, elbow, wrist, hip, knee, and ankle). The keypoints were normalized with respect to the left shoulder to remove translation and scaling effects.

- **DTW Alignment:**  
  After resampling the sequences to equal lengths, DTW was computed. The resulting DTW Distance Score was **140.83**, indicating that, despite minor differences in execution timing, the overall pose dynamics of the two videos are very similar.

- **Visualizations:**  
  Multiple DTW visualizations were generated including:
  - Time-Series Variation Plot
  - DTW Alignment Heatmap with Overlaid Alignment Path
  - DTW Alignment Scatter Plot
  - Frame Match Trace Plot
  - (Optionally) Cumulative DTW Cost Plot

> **[INFO] Logs from processing:**  
> ```
> [INFO] Processing video: video1.mp4
> [INFO] FPS: 30.07, Total Frames: 435, Duration: 14.47s
> [INFO] Keypoints saved to ../data/video1_keypoints.csv
> [INFO] Frames processed: 434, Time range: 0.00s to 14.40s
> 
> [INFO] Processing video: video2.mp4
> [INFO] FPS: 30.00, Total Frames: 1431, Duration: 47.70s
> [INFO] Keypoints saved to ../data/video2_keypoints.csv
> [INFO] Frames processed: 301, Time range: 21.00s to 31.00s
> 
> [INFO] Preprocessing keypoints...
> DTW Distance Score: 140.83
> ```

---

# Day 2 Returnables

This section contains the additional visual analysis and insights generated from the DTW alignment between the two pose sequences.

---

## Visualizations and Analysis

### 1. Time-Series Pose Variation Plot
- **Description:**  
  Displays the Euclidean distance between corresponding keypoints along the DTW alignment path.
- **Insights:**  
  The plot begins and ends with low distance values, indicating close alignment of the initial and final poses. However, a noticeable increase in distance in the middle of the alignment indicates some variation in motion between the two videos during that segment.
- **Possible Causes:**  
  - Differences in movement speed or timing mid-sequence.  
  - Variability in pose execution or subtle delays.  
  - Noise or inaccuracies in keypoint detection during complex or dynamic movements.

### 2. DTW Alignment Heatmap
- **Description:**  
  Shows the cost matrix representing the Euclidean distances between all frame pairs from both videos, with an overlay of the DTW alignment path.
- **Insights:**  
  The heatmap reveals a prominent diagonal band where the alignment cost is lowest. Minor deviations from the diagonal indicate slight mismatches in frame timing or pose execution, but overall, the alignment is good.
- **Possible Causes:**  
  - Small timing mismatches between the videos causing local misalignments.  
  - Slight differences in camera angle, zoom, or motion that result in discrepancies in keypoint values.  
  - Inconsistencies in the detection accuracy of the pose estimator during certain actions.

### 3. DTW Alignment Scatter Plot
- **Description:**  
  A scatter plot displaying the aligned frame indices from Video 1 against Video 2.
- **Insights:**  
  A close-to-diagonal linear trend confirms that the two sequences are largely synchronized, with only minor warping in some regions.
- **Possible Causes:**  
  - Minor pacing variations or differences in the onset of movements.  
  - Small differences in the segmentation of the action between the two videos.  
  - Noise in keypoint extraction leading to slight deviations in the alignment path.

### 4. Frame Match Trace Plot
- **Description:**  
  Visualizes the progression of matched frame indices along the DTW path.
- **Insights:**  
  A smooth, steadily increasing trace indicates consistent frame-to-frame alignment, with deviations highlighting sections where motion or timing differences occur.
- **Possible Causes:**  
  - Gradual changes in movement speed, such as accelerated or decelerated actions.  
  - Small interruptions or inconsistencies during certain key movements.  
  - Variations in how the pose is executed between the two sequences.

### 5. Overall GPT-4-Vision Analysis
> **GPT-4-Vision Analysis:**
> 
> The provided plots offer several insights into the alignment process of the two yoga pose sequences using Dynamic Time Warping (DTW):
> 
> - **Time-Series Pose Variation:**  
>   The plot shows that while the sequences are well aligned at the beginning and the end, significant discrepancies occur during the mid-section, suggesting differences in execution timing.
> 
> - **DTW Alignment Heatmap:**  
>   The cost matrix heatmap with the overlaid alignment path indicates that although the optimal path generally follows the diagonal, there are some deviations, meaning the two videos experience minor temporal stretching or compression.
> 
> - **Frame Match Trace:**  
>   The consistent diagonal trend in the matched frame indices confirms a generally linear relationship between the sequences, with slight early-stage divergence highlighting initial pacing differences.
> 
> In summary, the DTW score of **140.83** along with the visual analyses suggests that both videos capture the same action with high similarity overall; however, the mid-section exhibits some notable variation, potentially due to differences in movement execution or timing. This detailed alignment analysis verifies that the core movement is consistent across both videos, with only minor discrepancies.
---

## Deliverables (Day 2)
- **DTW Visualization Plots:**  
  - Time-Series Variation Plot (`outputs/time_series_variation.png`)
  - DTW Alignment Heatmap (`outputs/heatmap_with_values.png`)
  - DTW Alignment Scatter Plot (`outputs/dtw_alignment_scatter.png`)
  - Frame Match Trace Plot (`outputs/frame_match_trace.png`)
  - *(Optional)* Cumulative DTW Cost Plot (if implemented)
- **Insight Summary:**  
  The GPT-4-Vision Analysis detailing the strengths and minor variations in the pose alignment between the two videos.
- **Documentation:**  
  This detailed report is included in the README along with source code.

---

## Setup (Optional)
To run the notebook yourself, create and activate a Python virtual environment and install required libraries as specified in the Day 1 section.

```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```
open and write your openai api key in day 2.ipynb 
then run day 2.ipynb
