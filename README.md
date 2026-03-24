# 🎨 Painting Classification using Deep Learning

This project focuses on classifying paintings into artists using deep learning models. The goal is to analyze how different architectures perform on artistic image classification and to understand the trade-offs between model complexity and performance.

This project explores whether increasing model complexity (RNN, Attention) improves performance over strong CNN baselines.

---

## 📌 Project Overview

We compare three deep learning architectures:

- **ResNet18 (Baseline CNN)**
- **CNN + RNN (LSTM)**
- **CNN + RNN + Attention**

The models are evaluated using:
- Accuracy
- Precision, Recall, F1-score
- Confusion Matrix
- Top-k Accuracy
- Outlier Analysis
- Attention Visualization

---

## 📊 Dataset

The dataset consists of paintings from the following artists:

- Rene
- Titian
- Vincent

### Preprocessing:
- Images resized to **224×224**
- Normalization using ImageNet statistics
- Data augmentation applied:
  - Random cropping
  - Horizontal flipping
  - Rotation
  - Color jitter

---

## 🧠 Models Implemented

### 1. ResNet18 (Baseline)

- Pretrained on ImageNet
- Fine-tuned for classification
- Strong baseline with minimal complexity

---

### 2. CNN + RNN (LSTM)

- CNN extracts spatial features
- Features reshaped into sequences
- LSTM models spatial dependencies

---

### 3. CNN + RNN + Attention

- Adds attention mechanism on top of RNN
- Learns to focus on important regions of the image
- Provides interpretability via attention maps

---

## ⚙️ Training Details

- Loss Function: CrossEntropyLoss
- Optimizer: Adam
- Learning Rate: 0.0003
- Scheduler: StepLR (decay every 5 epochs)
- Epochs: 15

### Learning Rate Experiment (CNN+RNN)

Two learning rates were tested:
- **0.001** → Faster convergence but unstable
- **0.0003** → More stable and better generalization

---

## 📈 Results

| Model | Accuracy | F1 Score | Errors |
|------|--------|---------|--------|
| ResNet18 | 0.910 | 0.910 | 8 |
| CNN+RNN | 0.865 | 0.867 | 12 |
| CNN+RNN+Attention | 0.888 | 0.888 | 10 |

### Key Observations:
- ResNet18 achieves the best performance and stability
- CNN+RNN introduces unnecessary complexity
- Attention improves interpretability but not accuracy

---

## 📊 Evaluation Metrics

- Accuracy
- Precision, Recall, F1-score
- Confusion Matrix
- Top-k Accuracy (Top-3 and Top-5)

---

## 🔍 Error Analysis

Outliers were analyzed to understand model failures:

### Strong Outliers:
- High-confidence misclassifications
- Indicate systematic confusion between similar styles

### Weak Outliers:
- Low-confidence predictions
- Represent ambiguous or complex samples

### Insights:
- Errors are not random
- Most confusion occurs between visually similar artistic styles

---

## 🧭 Attention Visualization

The attention mechanism highlights regions important for prediction.

### Findings:
- The model often focuses on **texture and color patterns**
- Attention does not always align with the main subject
- Indicates reliance on **low-level features instead of semantic understanding**

---

## 💡 Key Insights

1. ResNet outperforms more complex architectures  
2. CNN+RNN does not improve performance due to mismatch with image structure  
3. Attention improves interpretability but not accuracy  
4. High Top-k accuracy indicates understanding of class similarity  
5. Errors are driven by stylistic similarities, not randomness  
6. Model performance saturates early (~10 epochs)  

---

## 🧠 Why CNN Outperforms CNN+RNN

- CNNs effectively capture spatial hierarchies  
- Images do not have a natural sequential structure  
- RNN introduces unnecessary complexity  
- Small dataset limits benefits of complex models  

---

## 🚀 Future Work

- Use Vision Transformers (ViT)  
- Explore CLIP-based models for semantic understanding  
- Multi-task learning (artist + style classification)  
- Larger datasets for better generalization  
- Contrastive learning for fine-grained classification  

---

## 📌 Conclusion

ResNet18 provides the best balance between performance, stability, and simplicity for this task.

More complex architectures like CNN+RNN and CNN+RNN+Attention do not outperform the baseline due to:
- Dataset size limitations  
- Lack of sequential structure in images  
- Increased model complexity  

These findings highlight that increased model complexity does not necessarily lead to better performance, particularly for smaller datasets. Carefully chosen simpler models can often provide more reliable and robust results.

This study emphasizes the importance of balancing model complexity with dataset characteristics when designing deep learning solutions.

---

## ⚡ How to Run

```bash
pip install -r requirements.txt
jupyter notebook
