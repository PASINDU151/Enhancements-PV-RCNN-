# PV-RCNN++ from Scratch (No OpenPCDet)

This repository provides a minimal, self-contained reimplementation of **PV-RCNN++** . The structure follows a clean modular format for training and evaluating 3D object detection models on the **KITTI dataset**.


## ⚙️ Environment Setup

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install torch torchvision torchaudio numpy opencv-python tqdm matplotlib
pip install -r requirements.txt

```

---
## Training - within the src directory use the below cmd

```bash
python -m src.train_model
```

## Evaluating - within the src directory use the below cmd

```bash
python -m src.evaluate_model
```

## 📦 Dataset Setup

Download the **KITTI 3D Object Detection Dataset** (Velodyne, labels, and calibration files).

**Official Link:**  
🔗 http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=3d

After download, arrange the folder as:

```
data/kitti/
│
├── velodyne/
│   ├── 000000.bin
│   ├── 000001.bin
│
├── label_2/
│   ├── 000000.txt
│   ├── 000001.txt
│
├── calib/
│   ├── 000000.txt
│   ├── 000001.txt
│
├── ImageSets/
│   ├── train.txt
│   ├── val.txt
│   ├── test.txt
```

---


## 🧠 Model Overview (Simplified)

The PV-RCNN++ architecture consists of:
1. **Voxel Set Abstraction** – Hybrid point-voxel feature encoding.  
2. **3D Backbone Network** – Sparse 3D CNN layers.  
3. **RPN (Region Proposal Network)** – Generates 3D proposals.  
4. **RoI Grid Pooling** – Samples local features.  
5. **VectorPool Attention** – Improved context fusion (core of PV-RCNN++).  
6. **Detection Head** – Final box regression + classification.

---

## 📈 Example Output (KITTI Format)

Example prediction file (`000000.txt`):

```
Car 0.00 0 -1.57 712.4 143.0 810.7 307.9 1.89 1.63 4.41 1.84 1.47 8.41 -1.56
```

---

## 🧹 Reset Everything

To completely reset all progress (model weights, logs, and results):

```bash
rm -rf experiments/*
rm -rf results/*
```

---

## 🧾 References

- [PV-RCNN++ Paper (arXiv:2102.00463)](https://arxiv.org/abs/2102.00463)
- [KITTI 3D Object Detection Dataset](http://www.cvlibs.net/datasets/kitti/)
- [Original PV-RCNN Paper](https://arxiv.org/abs/1912.13192)
