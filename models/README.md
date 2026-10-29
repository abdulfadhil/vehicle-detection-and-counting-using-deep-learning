# Model Weights

The application uses YOLOv8 model weights for vehicle detection. The README run examples use YOLOv8n, while the published sample results in `outputs/sample_fixed/` were generated using YOLOv8s.

**Required file:** `models/yolov8n.pt`

The model weights are excluded from this repository because of their size and separate distribution considerations.

To run the project:

1. Obtain YOLOv8n weights from a permitted source.
2. Place the file at `models/yolov8n.pt`.
3. Run the application using `--model models/yolov8n.pt`.

Check the applicable model licence and distribution terms before downloading or redistributing weights.