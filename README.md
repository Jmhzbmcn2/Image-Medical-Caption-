# Chest X-Ray Image Captioning

## 🩺 Project Description

This project develops an **Image Captioning** system applied in the medical field, specifically on **chest X-Ray images**.  
The goal of the system is:  
📷 ➡️ 📝 **From a single chest X-Ray image**, the model **automatically generates a medical report describing the patient's chest condition**, assisting doctors in diagnosis and patient monitoring.

## 📝 Task Overview

### Input and Output
- **Input:** Chest X-Ray images, which can be either frontal or lateral views.
- **Output:** A concise paragraph (text report) describing the patient's chest condition.

### Real-world Objective
- Assist doctors by automatically generating a preliminary report from chest X-Ray images.
- The model should be able to **identify different types of diseases** from the images.
- No image preprocessing, data augmentation (e.g., rotation, noise), or complex transformations are required.
- **Out-of-scope:** Bone fracture diagnosis is not handled.
- **In-scope:** Common thoracic diseases such as effusion, infiltration, pneumothorax, etc.

### Problem Approach

**Method 1: Traditional Encoder-Decoder Framework**
- **Encoder:** Extract visual features from the X-Ray image.
- **Decoder:** Generate textual reports based on extracted features.
- **Candidate Models:**
  - Encoder: Vision Transformer (ViT), DenseNet, ResNet
  - Decoder: LSTM, GPT-2
- **Evaluation:** Combine different encoder-decoder pairs and compare the results.

**Method 2 and Method 3: Vision-Language Models (VLMs)**
- **Method 2:** Use VLMs without fine-tuning to evaluate out-of-the-box performance.
- **Method 3:** Fine-tune VLMs specifically for chest X-Ray captioning.
- **Candidate VLMs:**
  - Fine-tunable: BLIP, BLIP-2, One-For-All
  - Non-fine-tunable (too large for this task): DeepSeek VL, QwenVL
- **Purpose of Method 2:** Show that general-purpose VLMs are not effective on domain-specific tasks.
- **Purpose of Method 3:** Demonstrate that fine-tuned VLMs significantly outperform traditional methods when adapted to chest X-Ray data.

### Datasets

- **Indiana University Chest X-Ray Dataset**
  - Contains frontal and lateral chest X-Ray images with accompanying reports.
  - Around 7,000 images — too small for full model training but useful for prototyping.
  
- **MIMIC-CXR Dataset**
  - Full dataset size: ~51 GB, over 300,000 images.
  - Selected subset: ~86,000 images with complete labels (using both "findings" and "impression" sections from reports).

