# Histopathology Image Classification

## Project Overview
This project develops machine learning models to analyze histopathology images (27×27 RGB) from colon tissue samples, performing two key classification tasks:
1. **Cell Type Classification**: Identifying specific cell types (fibroblast, inflammatory, epithelial, or others)
2. **Cancer Detection**: Determining if cells are cancerous or non-cancerous

The project implements baseline CNNs, advanced architectures with residual connections, and semi-supervised learning techniques to leverage unlabeled data.

## Dataset
- **Main Dataset**: 9,896 labeled images from 60 patients
- **Extra Dataset**: 10,384 unlabeled images from 38 patients
- **Image Size**: 27×27 RGB pixels
- **Classes**: 4 cell types (epithelial, inflammatory, fibroblast, others)
- **Cancer Labels**: Binary classification (cancerous/non-cancerous)

## Key Features
- Patient-aware data splitting to prevent data leakage
- Image quality assessment (blur, occlusion, edge detection)
- Data augmentation and class balancing techniques
- Baseline and advanced CNN architectures
- Semi-supervised learning with pseudo-labeling
- Robustness evaluation across image quality conditions

## Installation

### Prerequisites
- Python 3.7 or higher
- pip package manager

### Setup
1. Clone this repository
```bash
git clone <your-repo-url>
cd <project-directory>
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Organize your data structure
```
project/
├── Image_classification_data/
│   ├── data_labels_mainData.csv
│   ├── data_labels_extraData.csv
│   └── patch_images/
│       ├── 1.png
│       ├── 2.png
│       └── ...
├── requirements.txt
└── Image-classification-of-cancerous-cells.ipynb
```

## Usage

### Running the Notebook
```bash
jupyter notebook Image-classification-of-cancerous-cells.ipynb
```

### Key Steps in the Workflow
1. **Data Exploration**: Analyze class distribution and image quality
2. **Data Preprocessing**: Load, normalize, and augment images
3. **Baseline Models**: Train initial CNN models for both tasks
4. **Advanced Models**: Implement deeper architectures with regularization
5. **Semi-Supervised Learning**: Leverage unlabeled data with pseudo-labeling
6. **Evaluation**: Assess performance and robustness across image quality

## Model Performance

### Cell Type Classification
| Model | Macro F1 Score | Robustness Gap |
|-------|---------------|----------------|
| Baseline CNN | 0.5734 | 0.0142 |
| Advanced CNN | 0.5397 | 0.0631 |
| **Semi-Supervised** | **0.5917** | **0.0069** |

### Cancer Detection
| Model | F1 Score | Robustness Gap |
|-------|----------|----------------|
| Baseline CNN | 0.5976 | 0.2909 |
| **Advanced CNN** | **0.6885** | **0.1325** |

## Key Findings
- **Semi-supervised learning** achieved best results for cell type classification (3.2% improvement over baseline)
- **Advanced CNN** excelled in cancer detection (15.2% improvement over baseline)
- Cell type models showed good robustness to image quality variations
- Cancer models were more sensitive to blurry images, requiring quality-aware approaches

## Architecture Highlights

### Advanced CNN Features
- Residual connections for better gradient flow
- L2 regularization to prevent overfitting
- Progressive dropout (0.3 → 0.4 → 0.5)
- Global Average Pooling instead of flatten
- Cosine decay learning rate schedule

### Semi-Supervised Approach
- High-confidence pseudo-labeling (threshold: 0.8)
- 104% increase in training data
- Improved class balance without manual annotation
- Enhanced robustness to image quality variations

## Requirements
See `requirements.txt` for detailed dependencies. Main libraries:
- TensorFlow/Keras 2.8.0+
- OpenCV 4.5.0+
- scikit-learn 0.24.0+
- NumPy, Pandas, Matplotlib, Seaborn

## Future Improvements
- Test on larger input sizes (e.g., 75×75 pixels)
- Implement more sophisticated architectures (ResNet, DenseNet)
- Explore uncertainty quantification with Bayesian deep learning
- Develop specialized preprocessing for low-quality images
- Apply attention mechanisms for interpretability

## References
- Korbar et al. (2017) - Deep learning for colorectal polyp classification
- Rączkowska et al. (2019) - Bayesian deep learning for histopathology
- Maharana et al. (2022) - Data preprocessing and augmentation

---
**Note**: The models and techniques implemented here should be further validated before clinical use.
