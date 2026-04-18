🧾 PROJECT SPEC (CONDENSED)
🎯 Goal

Detect and track a given logo in a video without retraining per logo.

📥 Inputs
Reference logo image
e.g. logo.png
Video file
e.g. input.mp4
Config (optional)
thresholds (matches, inliers, score)
frame sampling rate
📤 Deliverables
1. Detection JSON

For each detection:

{
  "frame_idx": int,
  "timestamp": float,
  "track_id": int,
  "confidence": float,
  "bbox": [x1, y1, x2, y2],
  "polygon": [[x,y], [x,y], [x,y], [x,y]]
}
2. Annotated Video
draw polygon or bbox
show confidence + track ID
3. Summary Report (simple)
total detections
total visible duration
avg confidence
4. (Optional but strong) Evaluation
precision / recall on small labeled subset
failure examples
⚙️ Core Pipeline

For each frame:

Extract features (reference + frame)
Match features
Estimate homography (RANSAC)
Validate geometry
Compute confidence score
Keep / reject detection
Link detections across frames (tracking)
📏 Rules (VERY IMPORTANT)
Detection is VALID only if:
enough matches (e.g. > 20)
enough inliers after RANSAC
inlier ratio above threshold
projected polygon:
not degenerate
inside frame
reasonable size
Tracking rules:
same object across frames → same track_id
allow short gaps (missing frames)
remove one-frame noise detections
Scoring rules:

Combine:

match count
inlier ratio
temporal consistency
Performance rules:
must work on:
scale changes
perspective changes
moderate blur
must avoid:
random false positives
unstable detections
🧱 Minimum Viable Version (MVP)

You are DONE when you have:

detection working on video
homography-based localization
JSON output
annotated video
basic tracking
🚀 Strong Version (for CV impact)

Add:

modern matcher (LightGlue / LoFTR)
small evaluation dataset
comparison (baseline vs improved)
failure analysis
❌ Out of Scope
training custom logo detector
multi-logo system
production optimization
UI
🧠 What matters most

Not:

fancy models

But:

correct filtering
good geometry validation
clean pipeline
clear outputs