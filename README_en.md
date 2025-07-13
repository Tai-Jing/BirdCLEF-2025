# BirdCLEF 2025 Endangered Bird Audio Recognition Project

This project is a solution for the Kaggle BirdCLEF 2025 bird audio recognition competition, covering data preprocessing, feature extraction, model training, inference, and model conversion. **All code is organized as Jupyter Notebooks for easy reproduction of experiments.**

---

## 🌐 Language:
- [Chinese](README.md)
---

## 📂 Directory Structure

```
birdclef2025/
├── train/                  # Training notebooks
│   └── baseline_effinetb0_train.ipynb
├── inference/              # Inference/ensemble notebooks
│   ├── baseline_effinetb0_inference.ipynb
│   ├── ensembel_4_openvino.ipynb
│   └── ensemble_3_no_convert.ipynb
├── dataset/                # Reserved for datasets, download from the official website
├── data/                   # Data preprocessing notebooks and data
│   └── preprocess.ipynb
├── model_convert/          # Model conversion notebooks
│   ├── eca-nfnet.ipynb
│   ├── seresnext.ipynb
│   └── effinet.ipynb
├── requirements.txt        # Requirements list
├── .gitignore              # Git ignore file
├── README.md               # Project description
```

---

## 📊 Data Source

- **All data used in this project comes from the official open-source Kaggle dataset:**
  - BirdCLEF 2025 competition page: [https://www.kaggle.com/competitions/birdclef-2025/data](https://www.kaggle.com/competitions/birdclef-2025/data)
  - Preprocessed mel spectrogram dataset (optional): [https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms](https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms)

> ⚠️ **Note: All data paths in the notebooks use Kaggle platform defaults (e.g. `/kaggle/input/...`). Please modify the paths if running locally or in another environment.**

---

## 🚀 Main Workflow

### 1. Data Preprocessing
- Location: `data/preprocess.ipynb`
- Function: Convert raw audio data to mel-spectrograms for model training.
- Note: Supports processing only a subset (debug mode) or all samples. Can save as numpy format for efficient loading.

### 2. Training Baseline
- Location: `train/baseline_effinetb0_train.ipynb`
- Function: Multi-class bird audio classification training based on EfficientNet-B0, supporting 5-fold cross-validation, Mixup, and spectrogram augmentation.
- Note: Default parameters and paths are for Kaggle; modify paths for local use. Training results can be used directly for inference.

### 3. Inference Baseline
- Location: `inference/baseline_effinetb0_inference.ipynb`
- Function: Inference on test audio, generate submission files. Supports single model and ensemble inference.
- Note: Also uses Kaggle paths (not modified by author), supports TTA (test-time augmentation).

### 4. Model Conversion
- Location: `model_convert/`
- Function: Convert trained PyTorch models to OpenVINO and other formats for deployment and accelerated inference.

---

## 🛠️ Quick Start

1. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
2. **Data preparation**
   - Download the official Kaggle dataset
   - Optionally, download the preprocessed mel spectrogram dataset from Kaggle

3. **Run the workflow**
   - Run `data/preprocess.ipynb` for data preprocessing (or use the official mel spectrograms directly)
   - Run `train/baseline_effinetb0_train.ipynb` for model training
   - Run `inference/baseline_effinetb0_inference.ipynb` for inference and submission file generation

> ⚠️ **If running locally, please change all `/kaggle/input/...` paths in the notebooks to your local data paths.**

---

## 🙏 Acknowledgements
- Bird audio data and some baseline solutions are from the official and community open-source resources of Kaggle BirdCLEF 2025.

---

If you have any questions, please open an issue or contact the author (jingtai0427@gmail.com). 