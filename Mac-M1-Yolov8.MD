This documentation is based on the following documentations: 
- https://n-ahamed36.medium.com/running-yolov8-on-apple-silicon-with-mps-backend-a-simplified-guide-84b1d382f79c
- https://github.com/ultralytics/ultralytics?tab=readme-ov-file

Use the following steps to install and run yolov8 on an m1 mac. 

1. Install Python 3: https://www.python.org/downloads/
2. Create a folder in you mac. I created a folder called yolo.

  `mkdir yolo`

3. Go into folder

`cd yolo`

4. Place a generic video file in folder, like dog.mp4

5. download the model from here: https://github.com/ultralytics/ultralytics?tab=readme-ov-file 
   direct link to yolov8m.pt: https://github.com/ultralytics/assets/releases/download/v8.2.0/yolov8m.pt

6. Enter python enviornment: 
`python3`

7. Enter pythonn commands: 

- Step 1: Check MPS Availability
Before running YOLOv8, ensure your Apple Silicon GPU supports MPS

```
import torch

print(torch.backends.mps.is_available())
```

- Step 2: Install and import Required Libraries 
```
from ultralytics import YOLO
import torch
```

- Step 3: Load the YOLOv8 Model
Load a pre-trained YOLOv8 model using the Ultralytics library

```
from ultralytics import YOLO
model = YOLO('YOLOv8m.pt')  # Ensure you have the model file
```

- Step 4: Run Inference with MPS
Run YOLOv8 with MPS as the target device. This utilizes the Apple Silicon GPU for acceleration:

`results = model(source="input.mp4", show=True, conf=0.1, save=True, device='mps')`
