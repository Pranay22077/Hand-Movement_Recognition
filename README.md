# Hand Gesture Recognition System

![Python](https://img.shields.io/badge/python-3.7%2B-green.svg)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5%2B-red.svg)
![MediaPipe](https://img.shields.io/badge/MediaPipe-Latest-orange.svg)

A real-time hand gesture recognition system built with Python, OpenCV, and MediaPipe. This application can detect multiple hands simultaneously and recognize various hand gestures, including directional movements and specific finger positions.

## Features

- **Real-time Hand Tracking**: Detects and tracks hand movements in real-time using your webcam
- **Multi-hand Support**: Can track up to two hands simultaneously
- **Dynamic Gesture Recognition**: Recognizes hand movements in four directions (Up, Down, Left, Right)
- **Static Gesture Recognition**: Identifies specific finger positions for gestures like "Flip"
- **Visual Feedback**: Displays bounding boxes around detected hands and labels recognized gestures
- **Performance Monitor**: Shows FPS (Frames Per Second) counter for performance tracking

## Demo

[View Demo Video](https://github.com/Pranay22077/Hand-Movement_Recognition/blob/main/demo.mkv)

## Requirements

- Python 3.7+
- OpenCV (`cv2`)
- MediaPipe (`mediapipe`)
- A webcam or video input device

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/hand-gesture-recognition.git
   cd hand-gesture-recognition
   ```

2. Install the required packages:
   ```bash
   pip install opencv-python mediapipe
   ```

## Usage

Run the main script to start the application:

```bash
python hand_tracking.py
```

- Press 'q' to quit the application
- Position your hand(s) in front of the camera to see the tracking in action

## Gestures

The system can currently recognize the following gestures:

| Gesture | Description |
|---------|-------------|
| Up | Hand moving upward |
| Down | Hand moving downward |
| Left | Hand moving to the left |
| Right | Hand moving to the right |
| Stop | Hand not moving |

## Code Structure

- `HandTrackingDynamic` class: Core hand tracking and gesture recognition functionality
  - `__init__`: Initializes MediaPipe hands module with configurable parameters
  - `findFingers`: Processes video frames to detect hands
  - `findPosition`: Extracts hand landmark positions
  - `detectGesture`: Recognizes directional hand movements
  - `detectStop`: Identifies stationary hand position
  - `detectYoYo`: Recognizes the "Flip" gesture

- Helper functions:
  - `draw_text_with_outline`: Draws text with an outline for better visibility
  - `main`: Main execution loop that captures video and processes frames

## Customization

You can customize the detection parameters by modifying the `HandTrackingDynamic` class initialization:

```python
detector = HandTrackingDynamic(mode=False, maxHands=2, detectionCon=0.5, trackCon=0.5)
```

Parameters:
- `mode`: Processing mode flag
- `maxHands`: Maximum number of hands to detect (default: 2)
- `detectionCon`: Minimum detection confidence threshold (default: 0.5)
- `trackCon`: Minimum tracking confidence threshold (default: 0.5)

## Adding New Gestures

To add new gestures, create new detection methods in the `HandTrackingDynamic` class that analyze the relative positions of hand landmarks.

Example:
```python
def detectNewGesture(self):
    # Add your gesture detection logic here
    # using self.lmsList which contains all landmark coordinates
    pass
```

## Troubleshooting

- **Camera Not Found**: Ensure your webcam is properly connected and not being used by another application
- **Low FPS**: Lower the resolution in the `main()` function or use a more powerful computer
- **Detection Issues**: Try adjusting lighting conditions or detection confidence parameters

## Acknowledgments

- [MediaPipe](https://mediapipe.dev/) for the hand tracking solution
- [OpenCV](https://opencv.org/) for computer vision capabilities
