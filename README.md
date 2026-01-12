# Airplanes-detection-satellite-images
This repository contains all what I have used to create my own dataset and its use with the model for objects detection YOLOv8 .

## 1. Dataset Creation

### 1.1 Image Capture
Images were taken from Google Maps in different places around the world to create a dataset as diverse as possible. This includes:
> +100 images with airplanes (civilian and military)

> +100 images without airplanes

### 1.2 Preprocessing
Images were resized (960x960) and renamed using the script `images_prep.py`

### 1.3 Labeling
Images containing airplanes were manually labeled using [labelImg](https://github.com/HumanSignal/labelImg). And I obtained empty `.txt`files using `empty_files.py`

### 1.4 Labels and images are organized
I split the images and lables `.txt` in training and validation sets 
> 222 labeled images for training (82% aprox)

> 50 labeled images for validation (18% aprox)

### 1.5 `dataset.yaml` file
The dataset´s configuration file is written. It includes the path to the different folders and the names that receive the classes. In this case, only one class **0: airplane**


## 2. Detecting airplanes with YOLO
YOLOv8 is a real-time object detection algorithm based on convolutional neural networks developed by [Ultralytics](https://github.com/ultralytics/ultralytics).

### 2.1 Install the ultralytics package
```bash 
pip install ultralytics
```

### 2.2 Choose the model
YOLOv8 offers different models that vary in computational cost and accuracy. These models are designed to adapt to different scenarios, from resource-constrained devices to high-performance systems. In this project, the YOLOv8m (medium) version is used because it offers good accuracy with moderate computational cost.
> Note: For real-world applications, it may be worth testing more powerful models.

### 2.3 Training and detection
In the `yolo_detect.ipynb` notebook, the model is trained for 50 epochs, then the best result obtained is loaded and applied to detect airplanes in new satellite images.
> Note: It is not necessary to preprocess the images to test the model.

### 2.4 Print the Results
Seven images were used to evaluate the model:
- 5 with airplanes (17 in total)
- 2 without airplanes

**Correctly detected 16 out of 17 airplanes.**
