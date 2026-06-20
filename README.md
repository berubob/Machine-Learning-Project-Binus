# 🍔 Food Health Prediction Web App - Machine Learning

[![Deployment Status](https://img.shields.io/badge/Deployment-Vercel-black?style=for-the-badge&logo=vercel)]([https://your-vercel-link.vercel.app](https://machine-learning-project-binus.vercel.app/))
[![Academic Project](https://img.shields.io/badge/Binus%20University-Computer%20Science-blue?style=for-the-badge)](https://binus.ac.id/)

Aplikasi berbasis web cerdas untuk memprediksi klasifikasi tingkat kesehatan makanan (*Healthy* vs *Unhealthy*) secara real-time menggunakan model Machine Learning **Random Forest Classifier** yang diekspor ke dalam runtime format **ONNX (Open Neural Network Exchange)** untuk komputasi sisi klien yang efisien.

---

## 🚀 Fitur Utama
* **Real-time Client-Side Prediction:** Proses inferensi klasifikasi gizi dilakukan langsung di browser menggunakan `@onnxruntime/web`, mengurangi latensi jaringan secara signifikan.
* **Feature Engineering-Driven AI:** Memanfaatkan 4 metrik rasio makronutrisi tingkat lanjut untuk mempertegas batas keputusan (*decision boundary*) model.
* **Hybrid Architecture Safety Gating:** Mengintegrasikan gerbang aturan medis (*Rule Engine*) mutlak berbasis standar WHO sebelum data menyentuh lapisan model statistik.
* **Interactive Data Insights:** Pendukung dashboard analisis model dan dataset yang interaktif berbasis Streamlit.

---

## 📊 Hasil Evaluasi & Performa Model

Model dilatih menggunakan dataset yang berisi **2.395 sampel nutrisi** dengan distribusi kelas yang seimbang (1.311 Healthy vs 1.084 Unhealthy). Berdasarkan hasil eksperimen menggunakan 5-Fold Cross-Validation pada data pengujian (*Test Set*), **Random Forest Classifier** dipilih sebagai arsitektur final karena performanya yang stabil dan presisi.

### 1. Metrik Evaluasi Komprehensif
| Model Name | Accuracy | Precision | Recall | F1-Score | Status |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Random Forest Classifier** | **0.9916** | **0.9924** | **0.9916** | **0.9916** | **Selected (ONNX)** |
| **Gradient Boosting Classifier** | 0.9708 | 0.9721 | 0.9708 | 0.9707 | Baseline |

### 2. Matriks Kebingungan (Confusion Matrix)
Model Random Forest terbukti berhasil menekan angka kesalahan prediksi *False Positive* (makanan tidak sehat yang salah diklasifikasikan sebagai sehat) hingga tingkat minimum, mengunci akurasi operasional sistem pada level superior.

*Grafik perbandingan performa metrik dan visualisasi sebaran Confusion Matrix:*
