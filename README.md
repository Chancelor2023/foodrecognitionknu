# Japanese Food Recognition with YOLOv5

## Overview
This project focuses on the recognition of Japanese food using the YOLOv5 model. The UECFOOD256 dataset was used, containing 256 categories of food. The primary goal was to train and evaluate a YOLOv5 model for accurate food detection and classification.

## Results
- The training process resulted in a mean average precision (mAP) of `xx.x%` (example placeholder) across the dataset.
- Performance metrics were calculated, including precision, recall, and mAP at various IoU thresholds.

## Dataset
The dataset used is [UECFOOD256](https://www.kaggle.com/rkuo2000/uecfood256). It consists of 256 food categories and their bounding box annotations.

### Dataset Organization:
After preparation:
- `train`: 70% of the data.
- `val`: 20% of the data.
- `test`: 10% of the data.

Annotations were converted to YOLO format.

### Important Note:
In the data.yaml file used for the dataset configuration, make sure to modify line 12 as follows:  
Replace "3: 'chicken-'n'-egg'" with "3: 'chicken-egg'".  

## Installation and Usage
### Prerequisites:
1. Install the required Python packages:
   ```bash
   pip install ultralytics
   pip install kaggle

2. Download the dataset from Kaggle: Make sure you have your Kaggle API key (kaggle.json) saved in the appropriate directory. Then, download and extract the dataset:
   ```bash
   kaggle datasets download -d rkuo2000/uecfood256
   unzip uecfood256.zip -d dataset

3. Clone the YOLOv5 repository :
   ```bash
   git clone https://github.com/ultralytics/yolov5
   cd yolov5
   pip install -r requirements.txt

### Running the Project 
1. Prepare the dataset and annotations
   Organize the dataset into train, val, and test directories. Use the scripts provided in the notebook to convert the annotation format to YOLO format and split the dataset. For example:
   ```python
   Convert annotations to YOLO format
   python convert_annotations.py --dataset_path dataset --output_path yolo_annotations

2. Train the YOLOv5 model
   Run the training script with your dataset configuration :
   ```bash
   python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt

3. Evaluate the model
   Validate the model's performance on the test datatest :
   ```bash
   python val.py --weights runs/train/exp/weights/best.pt --data data.yaml

  4. Test on new images
     Run inference on custom images to see the model in action :
     ```bash
     python detect.py --weights runs/train/exp/weights/best.pt --source path_to_image_or_video

### Performance Metrics




