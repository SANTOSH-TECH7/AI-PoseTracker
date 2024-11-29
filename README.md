
# ReadMe: Pose Estimation and Curl Counter with Mediapipe

## Overview
This project utilizes the Mediapipe library to track body pose landmarks and calculate the number of bicep curls performed in real-time using a webcam. It displays key information such as the angle of the arm and the number of repetitions on the video feed.

## Features
- **Real-Time Pose Detection**: Tracks key body landmarks using Mediapipe's Pose solution.
- **Angle Calculation**: Computes the angle at the elbow joint to monitor arm movement.
- **Repetition Counter**: Counts the number of bicep curls performed based on arm movement.
- **User Feedback**: Displays the current count and stage ("up" or "down") on the video feed.

---

## Prerequisites

### Software Requirements
- Python 3.7 or later
- Webcam-enabled device
- Compatible operating system (Windows, macOS, Linux)

### Python Libraries
- `opencv-python`
- `mediapipe`
- `numpy`

You can install the required libraries using the following command:
```bash
pip install opencv-python mediapipe numpy
```

---

## How It Works

1. **Pose Tracking**: Mediapipe detects body landmarks such as the shoulder, elbow, and wrist.
2. **Angle Calculation**:
   - Uses trigonometric functions to calculate the angle at the elbow joint.
   - Identifies the arm's "up" or "down" stage based on the angle.
3. **Repetition Count**:
   - When the angle transitions from "down" (>160°) to "up" (<30°), a repetition is added to the counter.
4. **Visualization**:
   - Overlays the current angle, stage, and rep count on the video feed.
   - Displays pose landmarks for additional visual feedback.

---

## Usage Instructions

1. **Run the Script**:
   - Open a terminal or command prompt.
   - Run the script using the command:
     ```bash
     python pose_curl_counter.py
     ```

2. **Perform Curls**:
   - Position yourself in front of the webcam.
   - Start performing bicep curls. The program will track and count your reps.

3. **Exit**:
   - Press the `q` key to exit the program.

---

## Code Breakdown

### Main Components
- **`calculate_angle()`**:
  - Computes the angle between three points (shoulder, elbow, wrist).
- **Pose Detection**:
  - Mediapipe's `Pose` module identifies body landmarks in real-time.
- **Visualization**:
  - Displays the angle, stage, and repetition count on the video feed.
- **Curl Logic**:
  - Tracks the transition between "down" and "up" stages to count repetitions.

---

## Customization

- **Detection Confidence**:
  Adjust the `min_detection_confidence` and `min_tracking_confidence` in the `mp_pose.Pose` setup for sensitivity.
- **Angle Thresholds**:
  Modify the angle thresholds (`>160` for "down", `<30` for "up") to suit different workout styles.
- **Resolution**:
  Change the window resolution in the `cv2.VideoCapture()` setup for higher/lower quality.

---

## Troubleshooting

1. **No Webcam Detected**:
   - Ensure your webcam is properly connected and accessible.
   - Use the correct camera index in `cv2.VideoCapture(0)` (replace `0` with another index if needed).

2. **Slow Performance**:
   - Reduce resolution by scaling down the input frame.
   - Ensure no other heavy processes are running on your machine.

3. **Inaccurate Counting**:
   - Ensure the arm is clearly visible in the webcam feed.
   - Adjust lighting and background for better landmark detection.

---

## Example Output
- Real-time video feed with:
  - **Landmarks**: Visualized as dots connected by lines.
  - **Angle**: Displayed near the elbow.
  - **Repetition Count**: Displayed in a counter box on the top-left corner.
  - **Stage**: Current arm stage ("up" or "down").

---

## Future Enhancements
- Support for both arms.
- Real-time feedback on form or range of motion.
- Tracking multiple users.

---

## Acknowledgments
- **Mediapipe**: For providing the Pose Detection framework.
- **OpenCV**: For real-time video processing.

---

For questions or suggestions, feel free to contribute or reach out!
