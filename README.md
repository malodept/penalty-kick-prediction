# ⚽ Penalty Kick Prediction – Pose Estimation & Machine Learning

This project explores how a machine learning model can anticipate the direction of a penalty kick — **left**, **center**, or **right** — based solely on the **body movements** of the kicker *before the ball is hit*.

We assume that subtle pre-shot body cues can give away a player's intent. The goal is to test whether modern computer vision and sequence modeling techniques can pick up on those cues and outperform a random goalkeeper guessing strategy.

---

## Objectives

- Use **pose estimation** to extract the kicker's body position frame by frame
- Transform this temporal information into a structured dataset
- Train machine learning models to classify the direction of the kick
- Simulate and compare goalkeeper strategies
- Analyze individual player habits and deceptive movements

---

## Techniques Used

- **Pose Estimation**: with [YOLOv7-Pose](https://github.com/WongKinYiu/yolov7) for per-frame keypoint detection
- **Sequence Modeling**: LSTM, BiLSTM, GRU, and lightweight Transformer architectures
- **Model Evaluation**: accuracy, confusion matrices, and confidence analysis
- **Player Behavior Analysis**: comparison of pose and shot patterns across different players
- **Simulation**: strategies for goalkeepers based on prediction or statistics


---

## How It Works

1. **Data Preparation**: 
   - Large penalty compilations (e.g. "all Ronaldo penalties") are sliced into individual shots using `timecodes.txt`.
   - Each clip is labeled based on direction and player identity.

2. **Pose Extraction**:
   - YOLOv7-Pose runs on each video to output 17 keypoints per frame.
   - These are saved and structured into sequences of body positions.

3. **Dataset Construction**:
   - Each video is converted into a 2D array (frames × keypoints).
   - The final dataset contains many such sequences with direction labels.

4. **Model Training**:
   - LSTM-based models are trained to predict the direction from the pose sequence.
   - No ball, no goal, no contextual features — only the kicker’s motion.

5. **Evaluation & Analysis**:
   - Errors are analyzed to spot ambiguous or deceptive patterns.
   - Comparisons are made between players.
   - Simulated goalkeepers use random or informed strategies.

---

## Research Extensions

This project is also a starting point for deeper sports analytics questions:
- Are some players more predictable than others?
- Can we detect feints using temporal pose instability?
- Can we build a real-time assistant for goalkeeper training?
- Can this system generalize across camera angles, players, or match conditions?

---

## Notes

- This is an experimental project.
- All data comes from public video sources (e.g. YouTube).
- You need a working YOLOv7-Pose environment to reproduce results (see notebook 02).
