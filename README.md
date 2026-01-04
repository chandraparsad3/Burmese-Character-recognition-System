# Burmese Character Recognition System

This project builds a deep learning–based system to recognize Burmese characters from images.  
A custom Residual CNN model is trained from scratch to handle curved strokes, similar shapes, and diacritics in Burmese script.

---

## Dataset

- Source: https://www.kaggle.com/datasets/chandraparsad03/burmese-characterrs 
- Classes: 54  
- Images: ~12,000  
- Structure: One folder per character class

---

## Models

### Baseline Model
- Grayscale conversion + Sobel edge detection  
- 36-bin gradient histogram features  
- Dense (300, ReLU) → Dropout (0.2) → Softmax  
- Used only as a baseline; limited performance on complex characters

### Final Model (Main)
- Input: 64 × 64 × 3 images (normalized)
- Conv2D + BatchNorm + Swish
- Residual blocks with filters: 64 → 128 → 256 ×2 → 512
- Global Average Pooling
- Dense (1024, Swish) + Dropout (0.5)
- Softmax output (54 classes)

---

## Training

- Optimizer: Adam  
- Learning Rate: 0.0001  
- Loss: Categorical Cross-Entropy with label smoothing (0.1)  
- Batch Size: 32  
- Epochs: Up to 100  

Data Augmentation:
- Small rotation, shift, shear, and zoom  
- Nearest fill to preserve strokes

---

## Results

- Training Accuracy: ~99%  
- Validation Accuracy: ~95–96%  
- Classes: 54  

---

## Inference

- Resize image to 64×64  
- Normalize and predict class  
- Output label with confidence score

---
