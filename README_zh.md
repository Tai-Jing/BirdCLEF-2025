# BirdCLEF 2025 濒危鸟类音频识别项目 / Endangered Bird Audio Recognition

> **中文 | [English Version Below](#english-version)**

---

## 📂 目录结构 / Directory Structure

```
birdclef2025/
├── train/                  # 训练相关notebook / Training notebooks
│   └── baseline_effinetb0_train.ipynb
├── inference/              # 推理/集成notebook / Inference & ensemble notebooks
│   ├── baseline_effinetb0_inference.ipynb
│   ├── ensembel_4_openvino.ipynb
│   └── ensemble_3_no_convert.ipynb
├── dataset/                # 预留，存放数据集（需自行下载）/ For datasets (download from official site)
├── data/                   # 数据预处理notebook及数据 / Data preprocessing notebooks & data
│   └── preprocess.ipynb
├── model_convert/          # 模型转换notebook / Model conversion notebooks
│   ├── eca-nfnet.ipynb
│   ├── seresnext.ipynb
│   └── effinet.ipynb
├── requirements.txt        # 依赖包列表 / Requirements
├── .gitignore              # Git忽略文件 / Git ignore
├── README.md               # 项目说明 / Project readme
```

---

## 📊 数据来源 / Data Source

- **Kaggle BirdCLEF 2025 官方开源数据集 / Official Kaggle BirdCLEF 2025 dataset:**
  - [竞赛主页 / Competition page](https://www.kaggle.com/competitions/birdclef-2025/data)
  - [预处理mel频谱数据集 / Preprocessed mel spectrograms (optional)](https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms)

> ⚠️ **所有notebook中的数据路径均为Kaggle默认路径（如`/kaggle/input/...`），如在本地运行请自行修改。**
> ⚠️ **All notebook paths use Kaggle defaults (e.g. `/kaggle/input/...`), please change them for local use.**

---

## 🚀 主要流程 / Main Workflow

### 1. 数据预处理 / Data Preprocessing
- 位置 / Location: `data/preprocess.ipynb`
- 功能 / Function: 音频转mel频谱，为训练做准备。/ Convert audio to mel spectrogram for training.
- 说明 / Note: 支持debug模式与全量处理，可保存为npy。/ Supports debug/full mode, can save as npy.

### 2. 训练 Baseline / Training Baseline
- 位置 / Location: `train/baseline_effinetb0_train.ipynb`
- 功能 / Function: EfficientNet-B0多分类训练，支持5折交叉验证、Mixup、频谱增强等。/ EfficientNet-B0 multi-class training, 5-fold CV, Mixup, spec augment, etc.
- 说明 / Note: 默认Kaggle路径，本地需修改。/ Default Kaggle paths, change for local.

### 3. 推理 Baseline / Inference Baseline
- 位置 / Location: `inference/baseline_effinetb0_inference.ipynb`
- 功能 / Function: 测试集推理，生成提交文件，支持集成与TTA。/ Inference on test set, submission file, ensemble & TTA supported.
- 说明 / Note: 仍为Kaggle路径（作者懒得改了），如需本地运行请修改。/ Still Kaggle paths (not changed), modify for local use.

### 4. 模型转换 / Model Conversion
- 位置 / Location: `model_convert/`
- 功能 / Function: PyTorch模型转OpenVINO等格式，便于部署。/ Convert PyTorch models to OpenVINO etc. for deployment.

---

## 🛠️ 快速开始 / Quick Start

1. **安装依赖 / Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
2. **数据准备 / Data preparation**
   - 下载Kaggle官方数据集 / Download from Kaggle
   - 如需mel频谱数据集可额外下载 / Download mel spectrograms if needed
3. **运行流程 / Run workflow**
   - 运行`data/preprocess.ipynb`进行预处理 / Run `data/preprocess.ipynb` for preprocessing
   - 运行`train/baseline_effinetb0_train.ipynb`训练模型 / Run `train/baseline_effinetb0_train.ipynb` for training
   - 运行`inference/baseline_effinetb0_inference.ipynb`推理 / Run `inference/baseline_effinetb0_inference.ipynb` for inference

---

## 📦 依赖环境 / Requirements

详见`requirements.txt`，主要依赖如下 / See `requirements.txt`, main dependencies:
- torch, timm, librosa, opencv-python, pandas, scikit-learn, matplotlib, seaborn, tqdm

---

## 💡 其他说明 / Notes
- **数据和模型权重请勿上传到GitHub，已在.gitignore中屏蔽。**
- **Do NOT upload data or model weights to GitHub, already ignored.**
- `dataset/`目录可放自定义数据处理脚本。/ Use `dataset/` for custom data scripts if needed.
- notebook结构清晰，注释详细，便于理解和复现。/ Notebooks are well-structured and well-commented.

---

## 🙏 致谢 / Acknowledgement
- 鸟类声音数据及部分baseline方案来自Kaggle BirdCLEF 2025官方及社区开源资源。
- Bird audio data and some baselines from Kaggle BirdCLEF 2025 official & community resources.

---

如有问题欢迎提issue或联系作者(jingtai0427@gmail.com)。
If you have any questions, please open an issue or contact the author (jingtai0427@gmail.com).

---

# English Version

## 📂 Directory Structure

```
birdclef2025/
├── train/                  # Training notebooks
│   └── baseline_effinetb0_train.ipynb
├── inference/              # Inference & ensemble notebooks
│   ├── baseline_effinetb0_inference.ipynb
│   ├── ensembel_4_openvino.ipynb
│   └── ensemble_3_no_convert.ipynb
├── dataset/                # For datasets (download from official site)
├── data/                   # Data preprocessing notebooks & data
│   └── preprocess.ipynb
├── model_convert/          # Model conversion notebooks
│   ├── eca-nfnet.ipynb
│   ├── seresnext.ipynb
│   └── effinet.ipynb
├── requirements.txt        # Requirements
├── .gitignore              # Git ignore
├── README.md               # Project readme
```

## 📊 Data Source
- [Kaggle BirdCLEF 2025 Competition](https://www.kaggle.com/competitions/birdclef-2025/data)
- [Preprocessed mel spectrograms (optional)](https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms)

> ⚠️ All notebook paths use Kaggle defaults (e.g. `/kaggle/input/...`), please change them for local use.

## 🚀 Main Workflow
1. **Data Preprocessing**: `data/preprocess.ipynb` (audio to mel spectrogram)
2. **Training Baseline**: `train/baseline_effinetb0_train.ipynb` (EfficientNet-B0, 5-fold CV, Mixup, etc.)
3. **Inference Baseline**: `inference/baseline_effinetb0_inference.ipynb` (submission, ensemble, TTA)
4. **Model Conversion**: `model_convert/` (PyTorch to OpenVINO, etc.)

## 🛠️ Quick Start
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Download data from Kaggle
3. Run notebooks in order: preprocess → train → inference

## 📦 Requirements
See `requirements.txt`. Main dependencies: torch, timm, librosa, opencv-python, pandas, scikit-learn, matplotlib, seaborn, tqdm

## 💡 Notes
- Do NOT upload data or model weights to GitHub (see `.gitignore`).
- Use `dataset/` for custom data scripts if needed.
- Notebooks are well-structured and well-commented.

## 🙏 Acknowledgement
- Bird audio data and some baselines from Kaggle BirdCLEF 2025 official & community resources.

If you have any questions, please open an issue or contact the author (jingtai0427@gmail.com).



