# Fruit-vagitable_classificaition
# 🥝 Fruit & Vegetable Classification · Deep Learning Project

*A complete, production-ready computer vision pipeline for classifying images of fruits and vegetables into 36 classes, featuring transfer learning and an interactive Streamlit app.*

---

## 🌟 Overview

This repository contains a production-ready computer-vision pipeline that classifies images of **fruits and vegetables into 36 distinct classes** using transfer learning (MobileNetV2/EfficientNet) and serves predictions through a lightweight Streamlit web app.

**Use cases:**
- Automated checkout kiosks
- Quality-control lines in pack-houses
- Diet tracking or agricultural teaching aids

---

## 📋 Table of Contents
1. [Project Demo](#project-demo)
2. [Features](#features)
3. [Dataset](#dataset)
4. [Model Architecture](#model-architecture)
5. [Performance](#performance)
6. [Quick Start](#quick-start)
7. [Detailed Setup](#detailed-setup)
8. [Project Structure](#project-structure)
9. [Configuration](#configuration)
10. [Training & Evaluation](#training--evaluation)
11. [Streamlit App](#streamlit-app)
12. [Deployment Guide](#deployment-guide)
13. [Contributing](#contributing)
14. [License](#license)
15. [Contact](#contact)

---

## 🎥 Project Demo

| Local Streamlit                 | Cloud (Community)           |
|---------------------------------|-----------------------------|
| `streamlit run app.py`          | https://fruit-veg-classifier.streamlit.app |

*A demonstration GIF is available in `/docs/demo.gif`.*

---

## ✨ Features
- End-to-end pipeline: data download → augmentation → training → evaluation → one-click web app
- 36-class support (**10 fruits + 26 vegetables**)
- Transfer learning backbone (EfficientNet-B0 by default) for **95%+ macro F1** on validation set
- Modular training script (argparse/YAML config)
- Real-time inference (< 60 ms on CPU) with class-probability bar-chart
- Dockerfile & requirements-lock for reproducible builds
- CI workflow (GitHub Actions) runs linting + unit tests on every PR

---

## 📊 Dataset

| Property                 | Value                                         |
|--------------------------|-----------------------------------------------|
| Source                   | [Kaggle – *Fruit & Vegetable Image Recognition*](https://www.kaggle.com/datasets)  |
| Resolution (raw)         | 100 × 100 px (provided)                       |
| Classes (36)             | Fruits (10) & Vegetables (26)                 |
| Train / Val / Test split | 70% / 15% / 15%                           |
| Augmentations            | Random flip / rotate / color-jitter / cutout  |

> Need the data?  
> Run: `python tools/download_dataset.py --kaggle` (requires Kaggle API token)

---

## 🏗️ Model Architecture


---
Key hyper-parameters live in `configs/base.yaml` and are CLI-overridable.

---

## 📈 Performance

| Metric (Test set) | Score  |
|-------------------|--------|
| Top-1 Accuracy    | 96.3%  |
| Macro F1-score    | 95.8%  |
| Model size        | 14 MB  |
| Inference speed   | 57 ms / image (Ryzen 5 CPU) |

Confusion matrix & training curves are auto-saved to `runs/` (see `/docs/metrics/`).

---

## 🚀 Quick Start


---

## ⚙️ Detailed Setup

### Prerequisites
* Python 3.9+
* pip / conda
* (Optional) NVIDIA GPU + CUDA 11 for faster training
* Kaggle API token (for automatic data download)

### Environment Setup


---

## ⚙️ Configuration

All tunables are in `configs/`. Common flags:

| Flag                    | Default  | Description                                    |
|-------------------------|----------|------------------------------------------------|
| `model.name`            | effnet   | Base network: `mobilenet`, `effnet`, `resnet50`|
| `training.epochs`       | 25       | Training epochs                                |
| `training.batch_size`   | 32       | Mini-batch size                                |
| `dataset.img_size`      | 224      | Resize dimension                               |
| `optim.lr_initial`      | 1e-3     | Initial learning rate (Adam)                   |

CLI Override Example:

---

## 🗂️ Project Structure

Fruit-vagitable_classificaition/
│
├── data/ # (git-ignored) raw & processed images 
├── src/ # All source code
│ ├── datasets/ # Data preparation & loaders
│ ├── models/ # Model definitions & factory
│ ├── train.py # Main training entry-point
│ ├── predict.py # Single-image / batch inference
│ └── utils/ # Helpers, metrics, logging
│
├── app.py # Streamlit web interface
├── configs/ # YAML hyper-parameter sets
├── Dockerfile # Container for production
├── tests/ # Unit tests (pytest)
├── requirements.txt # Pinned runtime deps
├── environment.yml # Conda equivalent
└── README.md # ← you are here



---

## 🏋️‍♂️ Training & Evaluation

1. **Data preparation**  
2. **Training**  
TensorBoard logs (`--logdir runs/`) include LR-finder, aug-samples, per-class metrics.
3. **Evaluation**  
Returns:  
`{ "class": "Orange", "probability": 0.994 }`

---

## 🎛️ Streamlit App


Features:
- **Upload** any `.jpg/.png` or capture via webcam
- **Top-K chart**: probabilities over 36 classes
- **Model info**: version, input size, FPS, GPU usage

---

## ☁️ Deployment Guide

### Docker

### Streamlit Cloud
1. Push repo to GitHub
2. Create new app in **share.streamlit.io** pointing to `app.py`
3. Set env var `DATA_DIR` to `~/.cache/fruitveg/` (auto-download)

> For Heroku/Fly.io etc., see `/deploy/` templates.

---

## 🤝 Contributing

Have an idea? Want more augmentations, model support, UI tweaks?  
1. Fork → branch (`git checkout -b feat/my-feature`)
2. Run `make test` (ensure 0% lint errors)
3. Submit PR; CI runs style checks and unit tests

See `CONTRIBUTING.md` for full workflow and code style.

---

## 📜 License

Distributed under the **MIT License**.  
See `LICENSE` for details.

---

## 📞 Contact

**Aman Badhautiya** – [aman93977@gmail.com](mailto:aman93977@gmail.com)  
Project Link: [github.com/amanjigithub/Fruit-vagitable_classificaition](https://github.com/amanjigithub/Fruit-vagitable_classificaition)

> Built with ❤️ & TensorFlow. If this project helps you, please ⭐ the repo and share the demo!
