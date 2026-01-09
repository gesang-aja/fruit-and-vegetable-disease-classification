# Fruit and Vegetable Disease Classification (Healthy vs Rotten)

## 📌 Project Overview

This project focuses on **image classification of fruits and vegetables** to determine whether they are **Healthy** or **Rotten** using **Deep Learning**. The model is built with **Transfer Learning (MobileNetV2)** and trained on a curated subset of a Kaggle dataset.

The system classifies **6 classes**:

* Apple__Healthy
* Apple__Rotten
* Banana__Healthy
* Banana__Rotten
* Bellpepper__Healthy
* Bellpepper__Rotten

This project is developed as part of a **Dicoding / Bangkit Machine Learning submission** and follows best practices in data preparation, modeling, evaluation, and deployment.

---

## 👤 Author Information

* **Name**: Gesang Nur Zamroji
* **Email**: [gesang.23145@mhs.unesa.ac.id](mailto:gesang.23145@mhs.unesa.ac.id) | [m284d5y0685@student.devacademy.id](mailto:m284d5y0685@student.devacademy.id)
* **Dicoding ID**: M284D5Y0685

---

## 📂 Dataset

* **Source**: Kaggle – *Fruit and Vegetable Diseases Dataset (Healthy vs Rotten)*
* **Total Images**: 11,370 images
* **Classes**: 6

### Dataset Split

| Split      | Images | Percentage |
| ---------- | ------ | ---------- |
| Train      | 7,956  | 70%        |
| Validation | 1,703  | 15%        |
| Test       | 1,711  | 15%        |

The dataset is split **manually using Python** to ensure reproducibility.

---

## 🧪 Data Preprocessing & Augmentation

* Image resize to **224 × 224**
* Rescaling pixel values to **[0, 1]**
* Data augmentation techniques:

  * Rotation
  * Width & height shift
  * Shear & zoom
  * Horizontal flip
  * Brightness & channel shift

Implemented using `ImageDataGenerator`.

---

## 🧠 Model Architecture

* **Base Model**: MobileNetV2 (pretrained on ImageNet)
* **Transfer Learning**: Base model frozen
* **Custom Head**:

  * Conv2D + BatchNormalization + MaxPooling
  * GlobalAveragePooling
  * Dense (128) + Dropout (0.4)
  * Output Dense (Softmax – 6 classes)

### Optimizer & Loss

* Optimizer: **Adam (lr = 1e-3)**
* Loss Function: **Categorical Crossentropy**
* Metrics: **Accuracy**

---

## ⚙️ Training Strategy

* **Epochs**: 10
* **Callbacks**:

  * EarlyStopping (monitor: val_accuracy)
  * ModelCheckpoint (best model)
  * ReduceLROnPlateau
* **Class Weighting** applied to handle class imbalance

---

## 📊 Model Performance

| Dataset    | Accuracy   |
| ---------- | ---------- |
| Training   | **99.56%** |
| Validation | **98.59%** |
| Test       | **98.42%** |

The model demonstrates **excellent generalization** with minimal overfitting.

---

## 📈 Visualization

* Training vs Validation Accuracy
* Training vs Validation Loss
<img width="1790" height="790" alt="image" src="https://github.com/user-attachments/assets/931aa497-b270-4e55-a64b-7ab789cc630a" />



Used to monitor convergence and detect overfitting.

---

## 🔄 Model Conversion & Deployment

The trained model is exported into multiple formats:

### 1️⃣ TensorFlow SavedModel

```
submission/saved_model/
```

### 2️⃣ TensorFlow Lite (TFLite)

```
submission/tflite/model.tflite
submission/tflite/label.txt
```

### 3️⃣ TensorFlow.js

```
submission/tfjs_model/
```

All artifacts are compressed into:

```
submission_export.zip
```

---

## 🔍 Inference (Optional)

The project includes **TFLite inference testing** using sample test images to verify real-world usability.
<img width="323" height="411" alt="image" src="https://github.com/user-attachments/assets/0ee851e9-697a-4884-a1ed-73e93f0d4a87" />
<img width="417" height="411" alt="image" src="https://github.com/user-attachments/assets/bfedf676-44a7-44fd-8f93-2e5d1af983e1" />


---

## 🛠️ Tech Stack

* Python
* TensorFlow / Keras
* MobileNetV2
* NumPy, Pandas
* Matplotlib
* Scikit-learn
* TensorFlow Lite
* TensorFlow.js

---

## 📌 Conclusion

This project successfully demonstrates an **end-to-end image classification pipeline**, from dataset preparation to deployment-ready model formats. The achieved accuracy and robust generalization indicate that the model is suitable for real-world applications such as **food quality inspection systems**.

---

🚀 *This repository is ready for submission and portfolio use.*
