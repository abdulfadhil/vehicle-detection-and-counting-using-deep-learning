# Vehicle Detection and Counting Using Deep Learning

A computer-vision project that detects vehicles, tracks their movement, and counts virtual line crossings in traffic videos.

## About the Project

This academic project was developed in October 2023 to explore vehicle detection using deep learning. The current implementation combines vehicle detection, object tracking, and directional crossing counts to help analyse traffic video footage.

## The Problem

Manually observing traffic videos to identify vehicles and count their movement can be time-consuming. Vehicle movement can also be difficult to track consistently across video frames.

## The Solution

The system uses YOLOv8 to detect vehicles, ByteTrack to track them across frames, and a virtual line to count crossings by direction. It saves an annotated video and structured results for further review.

## Objectives

- Detect vehicles in video footage.
- Track detected vehicles across frames.
- Count virtual line crossings by direction.
- Save visual and structured outputs for review.

## How It Works

1. **Input:** Load a video file or connect a webcam.
2. **Detection:** YOLOv8 identifies vehicles in each frame.
3. **Tracking:** ByteTrack associates detections across frames.
4. **Counting:** The system records tracked vehicles crossing a virtual line.
5. **Output:** Save the annotated video, crossing-event CSV, and JSON summary.

## Key Features

- Vehicle detection using YOLOv8.
- Multi-object tracking using ByteTrack.
- Directional virtual line-crossing counts.
- Vehicle labels and tracking IDs.
- Annotated video output.
- CSV crossing events and JSON summaries.
- Video-file and webcam input.
- Configurable confidence threshold, image size, and line position.

## Tech Stack

- Python
- Ultralytics YOLOv8
- ByteTrack
- OpenCV
- NumPy
- pytest

## Screenshots

### Screenshot

![Vehicle detection and counting demo](docs/assets/vehicle-detection-demo.png)

## Demo

### Demo Video

[Watch the annotated demo video](outputs/sample_fixed/annotated.mp4)

## Sample Results

The included sample run produced the following results:

| Metric | Result |
|---|---:|
| Frames processed | 300 |
| Resolution | 640 × 360 |
| Video frame rate | 30 FPS |
| Crossing events | 14 |
| Cars counted | 13 |
| Trucks counted | 1 |

These are observed sample-run results, not model-accuracy measurements.

- [Crossing events CSV](outputs/sample_fixed/crossing_events.csv)
- [Run summary JSON](outputs/sample_fixed/summary.json)
- [Validation details](docs/validation.md)

## Getting Started

### Requirements

- Python 3.10 or later
- Compatible YOLO model weights

### Installation

Clone the repository and enter its directory:

```bash
git clone https://github.com/abdulfadhil/vehicle-detection-and-counting-using-deep-learning.git
cd vehicle-detection-and-counting-using-deep-learning
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it in Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

On Linux or macOS:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

## How to Run

### Process a Video

```bash
python run.py --source "path/to/video.mp4" --model "models/yolov8n.pt" --imgsz 320 --confidence 0.35
```

Replace the example video path with your input video.

### Use a Webcam

```bash
python run.py --source 0 --model "models/yolov8n.pt" --display
```

### Available Options

| Option | Purpose | Default |
|---|---|---|
| `--source` | Input video path or webcam index | Required |
| `--model` | YOLO model weights path | Required |
| `--output-dir` | Output directory | `outputs` |
| `--imgsz` | Inference image size | `640` |
| `--confidence` | Detection confidence threshold | `0.35` |
| `--line-position` | Counting-line position from `0` to `1` | `0.50` |
| `--display` | Display processed frames; press `q` to stop | Disabled |

Each run generates an annotated video, a crossing-event CSV, and a JSON summary in the selected output directory.

## Project Structure

```text
docs/
  assets/
    vehicle-detection-demo.png
  validation.md
models/
  README.md
outputs/
  sample_fixed/
    annotated.mp4
    crossing_events.csv
    summary.json
src/
  vehicle_flow/
tests/
run.py
requirements.txt
pyproject.toml
LICENSE
README.md
```

## Testing

Run the test suite:

```bash
python -m pytest -q
```

The tests cover counting logic, runner behaviour, and video input handling.

## Validation

The included validation notes describe the available sample run and its results. The reported counts represent observed virtual line crossings in that sample.

See [the validation details](docs/validation.md) for further information.

## Limitations

- Results depend on video quality, detections, tracking, model choice, and counting-line placement.
- The sample does not establish precision, recall, F1-score, ground-truth accuracy, or real-time performance.
- The system counts virtual line crossings; it does not measure calibrated physical traffic density.
- Model weights are not included in the repository. Obtain permitted weights and follow the guidance in [models/README.md](models/README.md).

## License

See [LICENSE](LICENSE) for the repository's license terms. Third-party libraries and model weights are subject to their own applicable terms.
