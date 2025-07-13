# BirdCLEF 2025 濒危鸟类音频识别

本项目为 Kaggle BirdCLEF 2025 鸟类声音识别竞赛的解决方案，涵盖数据预处理、特征提取、模型训练、推理、模型转换等流程。**所有代码均以 Jupyter Notebook 形式组织，便于复现实验。**

---

## 🌐 Language / 语言切换:
- [英文版本](README_en.md)

---

## 📂 目录结构

```
birdclef2025/
├── train/                  # 训练相关notebook
│   └── baseline_effinetb0_train.ipynb
├── inference/              # 推理/集成相关notebook
│   ├── baseline_effinetb0_inference.ipynb
│   ├── ensembel_4_openvino.ipynb
│   └── ensemble_3_no_convert.ipynb
├── dataset/                # 预留，存放数据集，数据集可以在官网自行下载
├── data/                   # 数据预处理notebook及数据
│   └── preprocess.ipynb
├── model_convert/          # 模型转换notebook
│   ├── eca-nfnet.ipynb
│   ├── seresnext.ipynb
│   └── effinet.ipynb
├── requirements.txt        # 依赖包列表
├── .gitignore              # Git忽略文件
├── README.md               # 项目说明
```

---

## 📊 数据来源

- **本项目所用数据均来自 Kaggle 官方开源数据集：**
  - BirdCLEF 2025 竞赛主页：[https://www.kaggle.com/competitions/birdclef-2025/data](https://www.kaggle.com/competitions/birdclef-2025/data)
  - 预处理后的 mel 频谱数据集（可选）：[https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms](https://www.kaggle.com/datasets/kadircandrisolu/birdclef25-mel-spectrograms)

> ⚠️ **注意：本项目所有 notebook 中的数据路径均为 Kaggle 平台默认路径（如 `/kaggle/input/...`），若在本地或其他环境运行，请自行修改数据路径。**

---

## 🚀 主要流程说明

### 1. 数据预处理
- 位置：`data/preprocess.ipynb`
- 功能：将原始音频数据转换为 mel-spectrogram（梅尔频谱），为后续模型训练做准备。
- 说明：可选择只处理部分样本（debug模式），或全部样本。支持保存为 numpy 格式，便于高效加载。

### 2. 训练 Baseline
- 位置：`train/baseline_effinetb0_train.ipynb`
- 功能：基于 EfficientNet-B0 的鸟类声音多分类训练，支持5折交叉验证、Mixup、频谱增强等。
- 说明：默认参数和路径均为 Kaggle 平台，(本地需修改路径)训练结果可直接用于推理。

### 3. 推理 Baseline
- 位置：`inference/baseline_effinetb0_inference.ipynb`
- 功能：对测试集音频进行推理，生成提交文件。支持单模型和多模型集成（Ensemble）。
- 说明：同样使用 Kaggle 路径（作者懒得改了），支持 TTA（测试时增强）。

### 4. 模型转换
- 位置：`model_convert/`
- 功能：将训练好的 PyTorch 模型转换为 OpenVINO 等格式，便于部署和加速推理。

---

## 🛠️ 快速开始

1. **安装依赖**
   ```bash
   pip install -r requirements.txt
   ```
2. **数据准备**
   - 下载 Kaggle 官方数据集
   - 如需使用预处理好的 mel 频谱数据集，可从 Kaggle 额外下载。

3. **运行流程**
   - 先运行 `data/preprocess.ipynb` 进行数据预处理（或直接用官方 mel 频谱）。
   - 运行 `train/baseline_effinetb0_train.ipynb` 进行模型训练。
   - 运行 `inference/baseline_effinetb0_inference.ipynb` 进行推理和生成提交文件。

> ⚠️ **如在本地运行，请将 notebook 中的所有 `/kaggle/input/...` 路径修改为你本地的数据实际路径。**

---


## 🙏 致谢
- 鸟类声音数据及部分 baseline 方案来自 Kaggle BirdCLEF 2025 官方及社区开源资源。

---

如有问题欢迎提 issue 或联系作者(jingtai0427@gmail.com)。



