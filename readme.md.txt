# Klasifikasi Buah & Sayur 6 Kelas Menggunakan Transfer Learning (MobileNetV2) + Custom CNN

Proyek ini bertujuan membangun model klasifikasi gambar untuk membedakan kondisi buah dan sayur ke dalam **6 kelas**. Model menggunakan kombinasi **Transfer Learning (MobileNetV2)** dan **Custom CNN** sehingga mampu mencapai akurasi sangat tinggi pada train, validation, dan test set.

---

##  1. Tujuan Proyek
Membuat sistem klasifikasi gambar buah dan sayur yang bisa mendeteksi kondisi (segmented ke 6 kelas) dengan tingkat akurasi tinggi, serta menyediakan model dalam format:

- **SavedModel**
- **TFLite**
- **TensorFlow.js (TFJS)**

serta melakukan **inference** pada gambar baru.

---

## 2. Dataset
Dataset terdiri dari **6 kelas**:

1.Apple_Healthy
2.Apple_Rotten
3.Banana_Healthy
4.Banana_Rotten
5.Bellpepper_Healthy
6.Bellpepper_Rotten


### Pembagian Data
| Split | Jumlah Gambar | | Persentase |
|------|---------------|-----------------|
| **Train** | 7.956 | | 0.7 |
| **Validation** | 1.703 | | 0.15 |
| **Test** | 1.711 | | 0.15 |

---

## 3. Arsitektur Model
Model menggabungkan:

### **Transfer Learning**
- Backbone **MobileNetV2 (imagenet, include_top=False)**
- Layer feature extractor dibekukan (frozen)

### **Custom CNN Layers**
Ditambahkan di atas backbone:

- `Conv2D`
- `BatchNormalization`
- `MaxPooling2D`
- `GlobalAveragePooling2D`
- `Dropout`
- `Dense Softmax (6 kelas)`

---

## 4. Training Setup

- **Optimizer**: Adam (lr=0.0001)  
- **Loss Function**: categorical_crossentropy  
- **Callbacks**:
  - EarlyStopping  
  - ModelCheckpoint  
  - ReduceLROnPlateau  

---

## 5. Hasil Training & Evaluasi

### 🔥 Akurasi Akhir
| Split | Akurasi |
|-------|---------|
| **Train** | **99.56%** |
| **Validation** | **98.59%** |
| **Test** | **98.42%** |

Model menunjukkan performa sangat baik dan tidak mengalami overfitting berlebihan berkat kombinasi augmentation, dropout, dan transfer learning.

---

## 6. Penyimpanan Model

Model berhasil diekspor ke 3 format berbeda:

## **SavedModel**  

## **TFLite (.tflite)**  

## **TensorFlow.js (TFJS)**  


---

## 🔍 7. Inference (Prediksi Gambar Baru)

Inference dilakukan menggunakan **TFLite**, karena paling ringan dan mudah digunakan di notebook.

### Contoh Output Inferensi
- Input: gambar dari folder test
- Output:
  - Nama kelas prediksi
  - Visualisasi gambar + label hasil prediksi

*(Contoh screenshot/plot disertakan di notebook)*

---
