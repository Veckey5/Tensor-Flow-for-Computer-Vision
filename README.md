<div align="center">

# 🖼️ Image Classification with TensorFlow & ResNet50

**Image processing · Pre-trained image recognition · Transfer learning · Data augmentation**

[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow%2FKeras-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![ResNet50](https://img.shields.io/badge/Model-ResNet50-6A5ACD)](https://keras.io/api/applications/resnet/)

</div>

## 📌 Project overview

This Jupyter notebook explores image classification using **Python, TensorFlow/Keras, and ResNet50**. It demonstrates how convolution filters transform image features, how a pre-trained ResNet50 model generates ImageNet predictions, and how transfer learning can be used for a two-class rural/urban image-classification task.

## 🔍 What the notebook covers

- **Image processing:** load and display sample images and apply convolution filters.
- **Pre-trained image recognition:** resize and preprocess images, then inspect the top-three ImageNet predictions from ResNet50.
- **Transfer learning:** use ResNet50 without its original classification head, freeze the pretrained feature extractor, and add a two-output softmax layer.
- **Image preparation:** load training and validation images from class-specific directories and resize them to `224 × 224` pixels.
- **Data augmentation:** apply horizontal flips and width/height shifts to training images.
- **Prediction inspection:** display validation images and print predicted class scores.

## 🧰 Tools and libraries

| Tool | Purpose |
|---|---|
| Python | Main programming language |
| TensorFlow / Keras | Model construction, image preprocessing, and training |
| ResNet50 | Pre-trained image recognition and transfer learning |
| NumPy | Image-array operations |
| Matplotlib / IPython | Notebook image display and visualisation |
| Jupyter Notebook | Interactive execution of the workflow |

## 📓 Main notebook

| File | Description |
|---|---|
| `Tensor Flow .ipynb` | Notebook containing convolution examples, ResNet50 inference, transfer learning, and data augmentation. |

## 🔄 Workflow

```text
Load and display images
          ↓
Apply convolution filters
          ↓
Preprocess images for ResNet50
          ↓
Inspect ImageNet predictions
          ↓
Build a two-class transfer-learning model
          ↓
Load training and validation images
          ↓
Apply augmentation to training images
          ↓
Inspect validation predictions
```

## 🗂️ Data schema

The notebook uses image files rather than a tabular CSV dataset. It references dog-breed images for image loading and pretrained ResNet50 inference, plus a rural/urban image collection for transfer learning. **The image datasets are not included in this repository.**

### Expected data directories

```text
dog-breed-identification/
├── train/
│   └── <image_id>.jpg
└── test/
    └── <image_id>.jpg

rural_and_urban_photos/
├── train/
│   ├── <class_name_1>/
│   │   └── <image_file>.jpg
│   └── <class_name_2>/
│       └── <image_file>.jpg
└── val/
    ├── <class_name_1>/
    │   └── <image_file>.jpg
    └── <class_name_2>/
        └── <image_file>.jpg
```

The class-specific subfolder names are used as labels by `flow_from_directory()`. The notebook configures two output classes; the exact class folder names and number of images are not specified in the notebook.

### Image-level schema

| Property | Description |
|---|---|
| Data unit | One image file |
| Image format | The examples use `.jpg` files |
| Model input size | `224 × 224` pixels |
| Image channels | RGB image data converted to numeric arrays |
| Preprocessing | ResNet50 `preprocess_input` |
| Label source | Class subfolder name, assigned by `flow_from_directory()` |
| Label encoding | Categorical (`class_mode='categorical'`) |
| Classifier output | Two softmax scores for the configured classes |
| ImageNet output | Top-three predicted ImageNet labels for sample images |

The `class_indices` property of the training and validation generators can be used to inspect the mapping between class names and numeric labels. The class mappings should be consistent between the two directories.

## 🏗️ Repository structure

Recommended GitHub layout:

```text
image-classification-resnet50/
├── README.md
├── Tensor Flow .ipynb
├── data/                         # Local datasets; not included in this repository
│   ├── dog-breed-identification/
│   │   ├── train/
│   │   └── test/
│   └── rural_and_urban_photos/
│       ├── train/
│       │   ├── <class_name_1>/
│       │   └── <class_name_2>/
│       └── val/
│           ├── <class_name_1>/
│           └── <class_name_2>/
└── .gitignore                    # Recommended for local data and notebook files
```

The `data/` folders show the expected local input layout; they are not part of the uploaded notebook. Large datasets and model weights should generally be kept out of Git unless their size and redistribution terms are appropriate.

## ⚙️ Setup and usage

### 1. Install the main packages

```bash
python -m venv .venv

# macOS / Linux
source .venv/bin/activate

# Windows
# .venv\Scripts\activate

python -m pip install --upgrade pip
pip install tensorflow numpy matplotlib jupyter
```

These are baseline dependencies, not a tested environment lockfile. The original notebook also relies on files and paths from a Kaggle environment and an external `learntools` helper module.

### 2. Prepare the data and resources

1. Obtain the required image datasets and arrange them as shown in the **Data schema** section.
2. Update hard-coded paths beginning with `/home/kaggle/` to match your environment.
3. Make the `learntools` helper module available for the convolution-filter exercise, or replace that exercise with an equivalent implementation.
4. Ensure the referenced ResNet50 weight files are available, or update the notebook to use a supported Keras weight-loading method.

### 3. Run the notebook

```bash
jupyter notebook
```

Open `Tensor Flow .ipynb` and run the cells in order after updating paths and dependencies.

---

<div align="center">

**Computer vision · Image preprocessing · Transfer learning · TensorFlow/Keras**

</div>
