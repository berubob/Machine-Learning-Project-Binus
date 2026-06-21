# Food Health Prediction Web App - Machine Learning - 4th Semester

[![Deployment Status](https://img.shields.io/badge/Deployment-Vercel-black?style=for-the-badge&logo=vercel)]((https://machine-learning-project-binus.vercel.app/))
[![Academic Project](https://img.shields.io/badge/Binus%20University-Computer%20Science-blue?style=for-the-badge)](https://binus.ac.id/)

Web based untuk memprediksi klasifikasi tingkat kesehatan makanan (*Healthy* vs *Unhealthy*) secara real-time menggunakan model Machine Learning **Random Forest Classifier** yang diekspor ke dalam runtime format **ONNX (Open Neural Network Exchange)**.

---

## Standarisasi Batasan Nutrisi (Nutritional Guidelines)

Penentuan label target pada arsitektur sistem ini diatur menggunakan fungsi logika matematika berlapis (*Ensemble Logic Gates*) yang merujuk pada regulasi medis dan badan gizi internasional resmi :

1. **Integritas Atwater Termodinamika Gizi (`Calorie_Anomaly_Score > 150`)**
   * *Formula:* $\text{Abs}(\text{Caloric Value} - [(\text{Fat} \times 9) + (\text{Carbohydrates} \times 4) + (\text{Protein} \times 4)]) > 150$
   * *Referensi:* **U.S. Department of Agriculture (USDA)** Atwater Factor Guide & **FAO Food and Nutrition Paper 77**.
2. **Plafon Energi Batas Maksimum Porsi (`Caloric Value > 800 Kcal`)**
   * *Referensi:* **Public Health England / NHS UK** (*"400-600-600 calorie rule"* untuk batas makan porsi tunggal berat) & **Kementerian Kesehatan RI (Kemenkes)** Angka Kecukupan Energi harian.
3. **Batas Konsumsi Gula Mutlak Tunggal (`Sugars > 40g`)**
   * *Referensi:* **World Health Organization (WHO)** Guideline: *"Sugars intake for adults and children"* (Membatasi gula bebas di bawah 10% total energi harian atau maksimal 50g per hari) & **Permenkes RI No. 30 Tahun 2013** tentang edukasi regulasi GGL.
4. **Batas Kepadatan Lemak Jenuh (`Fat > 35g`)**
   * *Referensi:* **American Heart Association (AHA)** / U.S. Dietary Guidelines (Konsumsi lemak total disarankan membatasi rentang maksimal harian sekitar 35% total kalori).
5. **Indeks Dominasi Gula Rafinasi (`Sugar_to_Carb_Ratio > 0.5`)**
   * *Referensi:* **Harvard T.H. Chan School of Public Health**: *"Carbohydrates and Blood Sugar"* (Mencegah lonjakan insulin akibat asupan karbohidrat kosong ber-Glycemic Index tinggi).
6. **Struktur Lemak Jenuh Berbahaya (`SatFat_to_TotalFat_Ratio > 0.4`)**
   * *Referensi:* **U.S. Food and Drug Administration (FDA)** Nutrition Facts Label Guide (Mengharuskan pembatasan konsumsi lemak jenuh/trans demi menjaga kesehatan jantung).
7. **Karbohidrat Kosong Olahan Refined Carbs (`Fiber_to_Carb_Ratio < 0.05` & `Carbohydrates > 30g`)**
   * *Referensi:* **The Dietary Guidelines for Americans** (Menyarankan rasio karbohidrat terhadap serat minimal berbanding 10:1 atau densitas serat di atas 0.10).

---
