<div align="center">

  <h1>☀️ Solarnet</h1>
  
  <p>
    <strong>Satellite Imagery Solar Panel Detection & Segmentation</strong>
  </p>

  <p>
    <a href="#-overview">Overview</a> •
    <a href="#-models">Models</a> •
    <a href="#-tech-stack">Tech Stack</a> •
    <a href="#-dataset">Dataset</a> •
    <a href="#-getting-started">Getting Started</a>
  </p>

  <p>
    <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white" alt="PyTorch" />
    <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white" alt="TensorFlow" />
    <img src="https://img.shields.io/badge/OpenCV-Computer_Vision-5C3EE8?style=flat&logo=opencv&logoColor=white" alt="OpenCV" />
    <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white" alt="Jupyter" />
  </p>
</div>

<br />

## 🚀 Overview

**Solarnet** is a deep learning initiative designed to automatically identify and segment solar panels from satellite or aerial imagery. 

With the rapid growth of renewable energy, maintaining an up-to-date registry of solar installations is crucial. This project leverages state-of-the-art semantic segmentation architectures to classify pixels as either "Solar Panel" or "Background," aiding in geospatial analysis and energy mapping.

## 🧠 Models Implemented

This repository explores two powerful architectures for semantic segmentation:

### 1. U-Net (TensorFlow/Keras)
* **Architecture:** Symmetric Encoder-Decoder with skip connections.
* **Details:** Custom implementation using `Conv2D`, `MaxPooling2D`, and `Conv2DTranspose` layers.
* **Best For:** Preserving fine spatial details, making it excellent for identifying the sharp edges of solar panels.

### 2. PSPNet (PyTorch)
* **Architecture:** Pyramid Scene Parsing Network.
* **Backbone:** ResNet18 (Pre-trained on ImageNet).
* **Library:** `segmentation-models-pytorch`.
* **Best For:** Capturing global context, helping distinguish solar panels from similar-looking rooftops or paved surfaces.

## 🛠 Tech Stack

| Component | Technology |
| :--- | :--- |
| **Deep Learning (Dynamic)** | PyTorch, segmentation-models-pytorch |
| **Deep Learning (Static)** | TensorFlow, Keras |
| **Image Processing** | OpenCV, PIL (Pillow) |
| **Data Handling** | NumPy, Scikit-Learn |
| **Visualization** | Matplotlib |

## 📂 Dataset Structure

The project expects the dataset to be organized in the following directory structure (specifically designed for `.bmp` images):

```text
Dataset/
└── Solar/
    ├── images/
    │   ├── image_01.bmp
    │   ├── image_02.bmp
    │   └── ...
    └── labels/ (Masks)
        ├── image_01.bmp
        ├── image_02.bmp
        └── ...
```````markdown
## Dataset Description

**Images:** RGB satellite imagery  
**Labels:** Grayscale masks where pixel value `> 0` indicates a solar panel

---

## 🚀 Getting Started

### Prerequisites
Ensure you have **Python** installed along with the required libraries.

---

### Installation

#### Clone the repository
```bash
git clone https://github.com/yourusername/solarnet.git
cd solarnet
````

#### Install dependencies

```bash
pip install torch tensorflow segmentation-models-pytorch opencv-python matplotlib scikit-learn
```

---

## Usage

### Open the Notebooks

You can run the experiments directly in **Jupyter Notebook** or **Google Colab**.

* `UNET_Solar.ipynb` – TensorFlow U-Net implementation
* `Solar_PSPNet.ipynb` – PyTorch PSPNet implementation

---

### Configure Paths

Update the `root_path` or `IMAGE_DIR` variables in the notebook to point to your local dataset location.

```python
# Example
train_image_dir = './Dataset/Solar/images'
train_mask_dir  = './Dataset/Solar/labels'
```

---

### Train

Run the training cells. The models will automatically resize images to **256×256** and begin training.

* **U-Net** saves the best model as `best_unet_model.h5`
* **PSPNet** uses `BCEWithLogitsLoss` and the **Adam** optimizer

---

## 📊 Results

The notebooks include visualization blocks that display:

* **Input Image:** The raw satellite photo
* **Ground Truth:** The actual location of solar panels
* **Prediction:** The model's segmentation output
