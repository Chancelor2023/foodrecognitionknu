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
The following performance metrics were observed after training :

- **Mean Average Precision (mAP@50):** 29.2%
- **Mean Average Precision (mAP@50-95):** 21.6%
- **Precision (P):** 32.9%
- **Recall (R):** 33.6%

Performance metrics were evaluated across 256 classes. Below is the performance breakdown per class:

| Class              | Precision (%) | Recall (%) | mAP@50 (%) | mAP@50-95 (%) |
|--------------------|---------------|------------|------------|---------------|
| Rice               | 25.1          | 89.5       | 31.4       | 24.1          |
| Eels               | 46.6          | 11.0       | 96.2       | 75.3          |
| Pilaf              | 15.3          | 66.7       | 22.3       | 20.4          |
| Chicken-Egg        | 16.6          | 50.0       | 22.3       | 19.6          |
| Pork               | 20.4          | 50.0       | 25.9       | 18.4          |
| Beef               | 29.0          | 33.3       | 32.5       | 26.7          |
| Sushi              | 62.9          | 50.1       | 53.9       | 19.8          |
| Chicken            | 27.9          | 33.3       | 86.3       | 57.2          |
| Fried              | 10.0          | 21.4       | 34.8       | 29.0          |
| Tempura            | 10.0          | 33.3       | 15.2       | 12.1          |
| Bibimbap           | 62.5          | 68.0       | 67.6       | 60.6          |
| Toast              | 16.7          | 50.0       | 15.2       | 9.72          |
| Croissant          | 52.4          | 50.0       | 50.4       | 37.5          |
| Roll               | 16.0          | 33.3       | 16.0       | 5.94          |
| Raisin             | 8.0           | 33.3       | 8.0        | 6.49          |
| Hamburger          | 40.9          | 78.6       | 48.5       | 33.7          |
| Pizza              | 51.6          | 45.9       | 47.2       | 41.5          |
| Sandwiches         | 31.2          | 83.3       | 66.4       | 44.1          |
| Udon               | 41.6          | 70.0       | 71.2       | 47.5          |
| Soba               | 39.2          | 72.7       | 73.3       | 47.6          |
| Ramen              | 31.6          | 58.8       | 46.4       | 37.1          |
| Tensin             | 56.8          | 98.9       | 88.8       | 54.3          |
| Spaghetti          | 38.3          | 20.0       | 24.7       | 19.5          |
| Japanese-style     | 24.1          | 75.0       | 26.7       | 14.6          |
| Takoyaki           | 36.1          | 50.0       | 26.6       | 18.9          |
| Sauteed            | 23.2          | 14.3       | 12.5       | 8.98          |
| Croquette          | 10.4          | 19.6       | 7.18       | 5.03          |
| Grilled            | 0.0           | 0.0        | 0.5        | 0.1           |
| Vegetable          | 24.0          | 20.0       | 11.9       | 7.24          |
| Miso               | 32.7          | 58.6       | 34.8       | 26.9          |
| Potage             | 34.6          | 100.0      | 79.4       | 30.9          |
| Sausage            | 21.3          | 16.7       | 10.1       | 6.04          |
| Oden               | 17.1          | 66.7       | 56.2       | 43.3          |
| Omelet             | 22.0          | 50.0       | 57.8       | 32.2          |
| Jiaozi             | 24.7          | 9.26       | 10.2       | 7.35          |
| Salmon             | 27.0          | 20.0       | 29.2       | 16.4          |
| Sukiyaki           | 32.5          | 28.6       | 30.9       | 23.4          |
| Sweet              | 17.9          | 57.1       | 46.8       | 38.3          |
| Lightly            | 100.0         | 0.0        | 25.9       | 20.6          |
| Steamed            | 10.3          | 16.7       | 24.1       | 15.5          |
| Sirloin            | 19.9          | 42.9       | 29.3       | 21.0          |
| Boiled             | 19.9          | 16.7       | 34.5       | 22.7          |
| Seasoned           | 9.88          | 25.0       | 33.5       | 28.4          |
| Hambarg            | 52.5          | 12.8       | 26.0       | 18.3          |
| Steak              | 42.5          | 62.0       | 43.7       | 24.2          |
| Dried              | 24.0          | 28.6       | 22.9       | 16.0          |
| Ginger             | 0.0           | 0.0        | 0.83       | 0.31          |
| Spicy              | 23.3          | 28.6       | 19.5       | 17.2          |
| Yakitori           | 33.7          | 50.0       | 49.6       | 35.9          |
| Cabbage            | 100.0         | 0.0        | 10.5       | 8.36          |
| Omelet             | 0.0           | 0.0        | 3.41       | 1.82          |
| Egg                | 33.3          | 45.5       | 41.4       | 19.1          |
| Natto              | 20.4          | 48.2       | 21.5       | 13.8          |
| Cold               | 9.55          | 25.0       | 16.8       | 7.97          |
| Chilled            | 36.2          | 85.9       | 63.7       | 55.0          |
| Stir-fried         | 60.6          | 16.7       | 31.0       | 21.3          |
| Simmered           | 11.3          | 16.7       | 25.0       | 19.0          |
| Boiled             | 35.3          | 66.7       | 58.2       | 39.2          |
| Sashimi            | 13.6          | 40.0       | 17.4       | 15.6          |
| Sushi              | 100.0         | 0.0        | 26.0       | 21.9          |
| Fish-shaped        | 20.9          | 25.0       | 13.9       | 12.1          |
| Shrimp             | 49.7          | 50.0       | 43.8       | 32.8          |
| Roast              | 47.8          | 23.9       | 35.0       | 24.3          |
| Steamed            | 20.1          | 28.6       | 15.3       | 5.52          |
| Cutlet             | 24.6          | 65.3       | 36.5       | 29.3          |
| Spaghetti          | 50.9          | 20.0       | 37.5       | 29.8          |
| Fried              | 18.9          | 20.0       | 15.4       | 9.37          |
| Potato             | 26.8          | 67.0       | 52.0       | 33.0          |
| Green              | 24.3          | 52.9       | 27.9       | 18.4          |
| Macaroni           | 48.6          | 42.9       | 42.8       | 30.6          |
| Japanese           | 13.0          | 40.0       | 11.9       | 8.99          |
| Pork               | 5.69          | 33.3       | 8.89       | 6.83          |
| Chinese            | 33.0          | 16.7       | 18.0       | 16.1          |
| Beef               | 17.4          | 60.0       | 27.9       | 21.3          |
| Kinpira-style      | 30.2          | 50.0       | 50.0       | 30.7          |
| Dipping            | 19.5          | 72.9       | 34.3       | 25.1          |
| Hot                | 55.9          | 25.0       | 19.8       | 14.6          |
| French             | 12.3          | 11.1       | 7.3        | 5.97          |
| Mixed              | 16.3          | 50.0       | 27.6       | 14.4          |
| Goya               | 26.6          | 60.0       | 44.1       | 36.3          |
| Green              | 100.0         | 0.0        | 13.2       | 10.7          |
| Okinawa            | 18.7          | 20.0       | 28.7       | 24.8          |
| Mango              | 9.57          | 33.3       | 39.0       | 5.7           |
| Almond             | 35.4          | 100.0      | 49.7       | 33.5          |
| Jjigae             | 30.7          | 55.5       | 26.1       | 23.4          |
| Dak                | 0.0           | 0.0        | 10.4       | 7.72          |
| Dry                | 45.8          | 28.6       | 31.4       | 25.5          |
| Kamameshi          | 23.0          | 28.6       | 33.5       | 20.0          |
| Paella             | 26.6          | 20.0       | 34.3       | 28.1          |
| Tanmen             | 4.96          | 16.7       | 9.99       | 5.53          |
| Kushikatu          | 33.7          | 44.4       | 52.6       | 34.7          |
| Yellow             | 0.0           | 0.0        | 5.53       | 3.33          |
| Pancake            | 12.9          | 66.7       | 26.8       | 22.0          |
| Champon            | 100.0         | 0.0        | 18.9       | 15.2          |
| Crape              | 100.0         | 0.0        | 5.01       | 3.68          |
| Tiramisu           | 22.4          | 100.0      | 79.5       | 66.3          |
| Waffle             | 33.0          | 33.3       | 24.8       | 19.6          |
| Rare               | 24.5          | 80.0       | 53.8       | 45.8          |
| Shortcake          | 44.8          | 66.7       | 55.0       | 47.5          |
| Mushroom           | 16.6          | 14.3       | 7.4        | 2.44          |
| Samul              | 27.2          | 51.4       | 22.7       | 21.2          |
| Zoni               | 22.1          | 60.0       | 23.5       | 19.1          |
| Fine               | 100.0         | 0.0        | 10.9       | 6.33          |
| Minestrone         | 12.8          | 20.0       | 6.83       | 5.34          |
| Pot                | 23.9          | 16.7       | 30.4       | 15.0          |
| Chicken            | 19.7          | 60.0       | 38.3       | 22.0          |
| Namero             | 66.8          | 60.0       | 60.1       | 51.5          |
| Broiled            | 45.4          | 100.0      | 94.3       | 86.3          |
| Clear              | 28.9          | 37.5       | 40.9       | 21.0          |
| Yudofu             | 13.8          | 75.0       | 38.8       | 28.9          |
| Mozuku             | 45.3          | 28.6       | 55.9       | 29.3          |
| Inarizushi         | 9.12          | 16.7       | 8.89       | 7.03          |
| Ham                | 8.37          | 25.0       | 13.6       | 8.18          |
| Minced             | 14.9          | 33.3       | 19.2       | 9.86          |
| Thinly             | 47.4          | 50.0       | 40.5       | 36.1          |
| Bagel              | 18.7          | 33.3       | 36.5       | 36.2          |
| Scone              | 33.6          | 28.6       | 27.9       | 24.7          |
| Tortilla           | 100.0         | 0.0        | 10.6       | 9.0           |
| Tacos              | 100.0         | 0.0        | 5.29       | 3.73          |
| Nachos             | 58.3          | 12.5       | 30.0       | 27.3          |
| Caesar             | 24.4          | 28.6       | 27.2       | 23.2          |
| Oatmeal            | 100.0         | 0.0        | 14.7       | 12.4          |
| Oshiruko           | 37.1          | 60.0       | 68.8       | 48.8          |
| Muffin             | 100.0         | 0.0        | 5.61       | 3.47          |
| Popcorn            | 25.1          | 50.0       | 54.0       | 45.8          |
| Doughnut           | 17.6          | 25.0       | 18.2       | 13.6          |
| Parfait            | 35.7          | 80.0       | 70.9       | 41.3          |
| Lamb               | 47.3          | 66.7       | 71.1       | 60.2          |
| Dish               | 16.1          | 41.9       | 32.4       | 27.7          |
| Xiao               | 42.1          | 85.7       | 74.2       | 62.3          |
| Moon               | 66.2          | 39.5       | 33.4       | 26.8          |
| Beef               | 25.1          | 66.7       | 40.1       | 30.9          |
| Fish               | 52.4          | 71.4       | 75.3       | 63.8          |
| Oyster             | 0.0           | 0.0        | 26.1       | 20.3          |
| Glutinous          | 12.2          | 50.0       | 19.9       | 16.6          |
| Stinky             | 100.0         | 0.0        | 26.1       | 21.3          |
| Lemon              | 81.9          | 33.3       | 36.4       | 28.8          |
| Khao               | 37.2          | 100.0      | 77.9       | 59.0          |
| Thai               | 39.6          | 84.5       | 61.7       | 56.1          |
| Boned              | 100.0         | 0.0        | 3.91       | 3.41          |
| Stir-fried         | 56.6          | 44.3       | 64.1       | 47.8          |
| Spicy              | 15.3          | 33.3       | 37.2       | 30.2          |
| Stewed             | 100.0         | 0.0        | 18.6       | 15.9          |
| Deep               | 24.5          | 60.0       | 23.4       | 20.5          |
| Barbecued          | 100.0         | 0.0        | 12.7       | 10.8          |
| Crispy             | 100.0         | 0.0        | 16.4       | 13.0          |
| Pho                | 18.4          | 85.7       | 51.5       | 40.6          |
| Hue                | 21.0          | 57.0       | 35.9       | 33.5          |
| Vermicelli         | 100.0         | 0.0        | 6.53       | 5.66          |
| Fried (twice)      | 10.1          | 14.3       | 19.3       | 13.6          |
| Steamed            | 100.0         | 0.0        | 29.8       | 45.7          |
| Shrimp             | 100.0         | 0.0        | 14.2       | 6.77          |
| Ball               | 7.89          | 16.7       | 12.7       | 7.87          |
| Coconut            | 36.1          | 50.0       | 34.7       | 23.4          |
| Small              | 19.4          | 62.5       | 68.6       | 54.9          |
| Glutinous          | 13.5          | 50.0       | 13.3       | 8.21          |
| Haupia             | 19.0          | 50.0       | 52.3       | 44.1          |
| Malasada           | 24.1          | 100.0      | 47.5       | 39.9          |
| Laulau             | 45.7          | 20.0       | 15.1       | 3.96          |
| Spam               | 20.8          | 11.1       | 28.8       | 19.6          |
| Oxtail             | 24.9          | 20.0       | 21.2       | 19.3          |
| Adobo              | 38.3          | 57.1       | 38.5       | 33.6          |
| Lumpia             | 9.96          | 50.0       | 57.2       | 51.5          |
| Brownie            | 52.3          | 66.7       | 57.4       | 45.3          |
| Churro             | 15.6          | 60.0       | 22.0       | 17.4          |
| Jambalaya          | 27.4          | 60.0       | 26.5       | 23.5          |
| Nasi               | 19.3          | 28.6       | 27.6       | 21.4          |
| Ayam               | 20.4          | 16.7       | 18.3       | 15.2          |
| Bubur              | 100.0         | 0.0        | 34.7       | 25.1          |
| Gulai              | 100.0         | 0.0        | 12.1       | 10.6          |
| Laksa              | 59.9          | 50.0       | 54.7       | 46.4          |
| Mie                | 29.9          | 100.0      | 56.6       | 41.0          |
| Babi               | 51.3          | 33.3       | 37.6       | 14.3          |
| Kaya               | 48.7          | 83.3       | 62.5       | 50.8          |
| Curry              | 35.2          | 50.0       | 43.6       | 36.6          |
| Chow               | 28.2          | 83.3       | 71.6       | 62.0          |
| Zha                | 66.6          | 25.0       | 64.8       | 38.8          |
| Kung               | 35.0          | 75.0       | 62.2       | 35.0          |
| Crullers           | 17.4          | 50.0       | 13.9       | 10.4          |
| Eggplant           | 100.0         | 0.0        | 16.9       | 12.9          |
| Bean               | 10.0          | 100.0      | 18.7       | 8.54          |
| Salt               | 21.9          | 16.7       | 25.9       | 18.3          |
| Baked              | 64.4          | 22.2       | 28.0       | 16.4          |
| Braised            | 29.9          | 27.1       | 21.9       | 17.3          |
| Winter             | 27.5          | 42.9       | 55.0       | 40.7          |
| Chinese            | 31.8          | 57.1       | 56.2       | 46.2          |
| Eight              | 9.97          | 20.0       | 13.2       | 9.04          |


## File structure
The repository contains the following files and folders :

- **README.md**: Project documentation (this file).
- **Japanese_food_recognition.ipynb**: The Jupyter Notebook containing the full implementation.
- **data.yaml**: Dataset configuration for YOLOv5.
- **runs/**: Folder containing training results, including the best model weights.
- **dataset/**: Folder containing the dataset and annotations.


## References
The following resources were used in this project:

- [YOLOv5 Documentation](https://github.com/ultralytics/yolov5): Official YOLOv5 documentation.
- [UECFOOD256 Dataset](https://www.kaggle.com/rkuo2000/uecfood256): UECFOOD256 dataset on Kaggle.
- [Kaggle API](https://www.kaggle.com/docs/api): Official Kaggle API documentation for dataset management.


## Issues and Future Work

### Known Issues:
- **Imbalanced Data**: Some food categories have very few examples, which can lead to lower precision and recall for those classes.
- **Model Overfitting**: Despite regularization and augmentation, overfitting may occur for smaller classes.

### Future Work:
- **Increase Dataset Size**: Adding more food images to the dataset could improve the model's performance, especially for underrepresented categories.
- **Experiment with Other YOLO Architectures**: Exploring advanced versions like YOLOv8 could provide better performance and faster inference times.
- **Model Deployment**: Consider deploying the trained model as a web application or a mobile app for real-time food recognition.
