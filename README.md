# YOLO Model Training and Inference Pipeline with Streamlit

Welcome to the **YOLO Model Training and Inference Pipeline**!

This project is designed to simplify the training and inference processes of YOLO models using Streamlit, providing a user-friendly interface for both novice and experienced users. This allows users to train YOLO models and obtain inferences from their trained models using an intuitive user interface. This pipeline supports uploading pre-trained models or custom-trained models, handling dataset preparation, and visualizing results efficiently.

## 🚀 Overview

This repository contains a Streamlit application that enables users to:
- **Train YOLO models** using custom datasets or pre-trained models from Ultralytics.
- **Perform inference** on images using trained models.
- **Visualize results** and adjust bounding box coordinates easily.

## 🎯 Key Features

- **Choose Pre-Trained Models**: Select from various YOLOv8 and YOLOv10 models based on your requirements:
  - `yolov8n.pt`: YOLOv8-N (Nano) ~3.2 M Params
  - `yolov8s.pt`: YOLOv8-S (Small) ~11.2 M Params
  - `yolov8m.pt`: YOLOv8-M (Medium) ~25.9 M Params
  - `yolov8l.pt`: YOLOv8-L (Large) ~43.7 M Params
  - `yolov8x.pt`: YOLOv8-X (Extra-large) ~68.2 M Params
  - `yolov10n.pt`: YOLOv10-N (Nano) ~2.3 M Params
  - `yolov10s.pt`: YOLOv10-S (Small) ~7.2 M Params
  - `yolov10m.pt`: YOLOv10-M (Medium) ~15.4 M Params
  - `yolov10l.pt`: YOLOv10-L (Large) ~24.4 M Params
  - `yolov10x.pt`: YOLOv10-X (Extra-large) ~29.5 M Params

- **Upload Custom Model**: Have a pre-trained model in .pt format? Easily upload it for training or inference.

- **Upload Custom Dataset**: Upload your dataset in a structured format, including training, validation, and test images along with their coordinates.

- **Data Augmentation**: Apply real-time transformations to images and visualize changes live on a sample image.

- **Interactive UI**: Modify bounding box properties, such as color, thickness, and label size, and visualize inference results in real time on a sample image.

- **Non-Maximum Suppression (NMS)**: Combine overlapping bounding boxes based on a user-defined threshold during the inference process, ensuring a cleaner and more accurate output.

- **Output Files**: Download results in a .zip format containing processed images with bounding boxes and metadata in a CSV file for further analysis.

## 📦 Requirements

To run this project, you'll need the following Python packages:

- Streamlit
- Ultralytics
- OpenCV
- Pandas
- NumPy
- Torch

### Training YOLO Models

- Upload your dataset as a `.zip` file containing images and their coordinates.
- Select the pre-trained model or upload your own `.pt` file.
- Apply transformations to the images and visualize results on a sample before running them on all images.
- Choose the number of epochs and start training.

### Running Inference

- Upload your trained YOLO model and test dataset.
- Adjust bounding box properties using sliders and visualize results on a sample before running on all images.
- Select a threshold for Non-Maximum Suppression to combine overlapping bounding boxes during inference.

## 📄 Output

- After training, download a `.zip` file containing the trained model and results.
- The inference process generates a `.zip` file with processed images and a CSV containing prediction data.

## 📚 Documentation

For a detailed demonstration and interactive usage, refer to the [YOLO-Streamlit-Pipeline-Notebook](YOLOMeetsStreamlit.ipynb) Jupyter Notebook.

## 📈 Running the Streamlit App on Google Colab

This guide will walk you through the steps to run your Streamlit app using Google Colab. By following these steps, you can easily set up your environment and access the app via a web browser.

## 🛠 Installation Steps

Follow the steps below to get your Streamlit app up and running on Google Colab.

### Step 1: Install Localtunnel

Localtunnel allows you to share your localhost server over the web. To install Localtunnel, run the following command in a Colab cell:

```python
!npm install localtunnel
```

### Step 2: Retrieve the External URL

Once Localtunnel is running, check the logs to retrieve the external URL. You can view the logs by running:

```python
!streamlit run app.py &>/content/logs.txt &

!cat logs.txt
```

You should see an output similar to:

```
You can now view your Streamlit app in your browser.

  Local URL: http://localhost:8501
  Network URL: http://172.28.0.12:8501
  External URL: http://34.73.158.238:8501
```

In this example, the token value you'll need for the next steps is `34.73.158.238`.

### Step 3: Start Localtunnel

After installing Localtunnel, start it by executing the command below. This will create a secure tunnel to your Streamlit app:

```python
!npx localtunnel --port 8501
```

You should see an output similar to:

```
your url is: https://rotten-taxes-dance.loca.lt
```

- **Click on the provided URL** (e.g., `https://rotten-taxes-dance.loca.lt`).
- A new tab will open, prompting you to enter your token.

### Step 4: Enter the Token

Input the token you retrieved earlier (e.g., `34.73.158.238`) into the prompt that appears. Once you enter the token, your Streamlit app will launch directly in the browser.

### 🚀 Future Updates

In addition to the current features, several enhancements are planned for the project:

1. **Update Coordinate Files During Transformations**:
   - Ensure that any transformations applied to images also update the associated `.txt` coordinate files. This will maintain consistency between the images and their annotations.

2. **Upload Predicted Images and Annotate Accurately**:
   - Users will soon be able to upload images that already have predicted boundary boxes. They can also upload a corresponding `.csv` file containing the coordinates for each bounding box.
   - This feature will allow users to visually adjust the boundary boxes by modifying the coordinates (x0, x1, y0, y1). 
   - After making adjustments, users will receive a `.zip` file containing:
     - An updated `.csv` file with the new coordinates.
     - A folder with separate `.txt` files for each image, containing the updated coordinates for direct use in training the YOLO model.

These upcoming features will help streamline the workflow for users, saving them time and ensuring more accurate results when training and using YOLO models.
