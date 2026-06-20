# Machine-Learning-Project-Binus
## 📚 Standarisasi Batasan Nutrisi & Referensi Ilmiah (Nutritional Guidelines)

Penentuan kelas target `Healthy` dan `Unhealthy` pada proyek ini diatur menggunakan fungsi keputusan berlapis (*Ensemble Logic Gates*) yang didasarkan pada standar kesehatan internasional, regulasi medis, serta hukum fisik gizi. 

Berikut adalah detail penjelasan, kalkulasi matematika, dan referensi resmi untuk **7 Benteng Aturan Batasan Threshold**:

### 1. Deteksi Integritas Data (Calorie Anomaly Score > 150)
* **Logika & Kalkulasi:** Rumus ini menggunakan **Sistem Atwater Fisik Gizi** untuk menghitung ekspektasi energi riil dari makronutrisi.
    $$\text{Calculated Calories} = (\text{Fat} \times 9.0) + (\text{Carbohydrates} \times 4.0) + (\text{Protein} \times 4.0)$$
    Jika selisih absolut antara nilai kalori label dan kalkulasi fisik lebih besar dari 150 Kcal, data dianggap cacat/palsu (*anomali*).
* **Referensi Resmi:** * *Food and Agriculture Organization (FAO)*: "Food energy - methods of analysis and conversion factors" (FAO Food and Nutrition Paper 77).
    * *U.S. Department of Agriculture (USDA)* Atwater System Factor Guide.

### 2. Plafon Kalori Maksimum Sekali Makan (Caloric Value > 800 Kcal)
* **Logika & Kalkulasi:** Membatasi asupan energi total dalam satu porsi makanan tunggal tunggal agar tidak memicu lonjakan insulin ekstrem dan penumpukan lemak visceral.
* **Referensi Resmi:**
    * *National Health Service (NHS) UK / Public Health England*: Panduan *"Rule of Thumb: 400-600-600"* merekomendasikan porsi makan malam/siang berat ideal berada di kisaran 600 Kcal. Nilai $>800\text{ Kcal}$ dalam satu menu tunggal dikategorikan sebagai *over-density energy* (kepadatan energi berlebih).
    * *Kementerian Kesehatan Republik Indonesia (Kemenkes RI)*: Angka Kecukupan Energi (AKE) harian rata-rata dewasa (~2100 Kcal), di mana porsi makan besar ideal adalah sepertiganya (~700 Kcal).

### 3. Batas Gula Mutlak (Sugars > 40g)
* **Logika & Kalkulasi:** Makanan atau minuman kemasan tunggal yang menghabiskan jatah kuota harian gula dalam sekali konsumsi langsung divonis tidak sehat untuk mencegah risiko Diabetes Melitus Tipe 2.
* **Referensi Resmi:**
    * *World Health Organization (WHO) Guideline*: "Sugars intake for adults and children". WHO merekomendasikan pembatasan gula bebas (*free sugars*) di bawah 10% dari total energi harian, atau setara maksimal **50 gram per hari** (dan idealnya di bawah 25 gram untuk manfaat tambahan).
    * *Peraturan Menteri Kesehatan RI (Permenkes) No. 30 Tahun 2013*: Sosialisasi batasan konsumsi Gula, Garam, Lemak (GGL) per hari adalah **G4 (4 sendok makan gula / 50 gram)**.

### 4. Batas Lemak Total Per Porsi (Fat > 35g)
* **Logika & Kalkulasi:** Membatasi makanan padat minyak atau produk olahan *deep-fried* yang menyumbang kalori kosong dari asam lemak trans jahat.
* **Referensi Resmi:**
    * *American Heart Association (AHA) / U.S. Dietary Guidelines*: Konsumsi lemak total harian disarankan berkisar antara 20% hingga 35% dari total kalori harian (sekitar 65 gram untuk diet 2000 Kcal). Satu makanan tunggal yang mengandung lemak $>35\text{g}$ berarti telah menghabiskan lebih dari setengah kuota harian.

### 5. Dominasi Gula terhadap Karbohidrat (Sugar to Carb Ratio > 0.5)
* **Logika & Kalkulasi:** Memastikan karbohidrat didominasi oleh karbohidrat kompleks, bukan gula sederhana/rafinasi yang memiliki *Glycemic Index* (GI) tinggi.
    $$\text{Ratio} = \frac{\text{Sugars}}{\text{Carbohydrates}}$$
* **Referensi Resmi:**
    * *Harvard T.H. Chan School of Public Health*: "Carbohydrates and Blood Sugar". Mengonsumsi makanan dengan kandungan gula lebih dari setengah total karbohidratnya memicu lonjakan glukosa darah secara drastis.

### 6. Batas Rasio Lemak Jenuh (SatFat to TotalFat Ratio > 0.4)
* **Logika & Kalkulasi:** Mengidentifikasi apakah struktur lemak makanan didominasi oleh lemak jenuh berbahaya (*saturated fats*) yang biasa ditemukan pada minyak goreng bekas atau mentega berlebih.
    $$\text{Ratio} = \frac{\text{Saturated Fats}}{\text{Total Fat}}$$
* **Referensi Resmi:**
    * *U.S. Food and Drug Administration (FDA)*: "Saturated Fat Guidelines on Nutrition Facts Label". FDA dan AHA menegaskan konsumsi lemak jenuh harus dibatasi di bawah 10% total kalori (sekitar 20g per hari), dan struktur komposisi lemak yang sehat harus didominasi oleh lemak tak jenuh (*unsaturated fats*).

### 7. Karbohidrat Kosong Miskin Serat (Fiber to Carb Ratio < 0.05 & Carbohydrates > 30g)
* **Logika & Kalkulasi:** Menyaring produk tepung-tepungan olahan (*refined carbohydrates*) tinggi karbohidrat (>30g) namun miskin serat alami (rasio serat di bawah 5%).
    $$\text{Ratio} = \frac{\text{Dietary Fiber}}{\text{Carbohydrates}} < 0.05$$
* **Referensi Resmi:**
    * *The Dietary Guidelines for Americans*: Menyarankan rasio karbohidrat terhadap serat minimal ideal adalah **10:1** (atau rasio serat terhadap karbohidrat sebesar **0.10**). Batas $0.05$ digunakan sebagai batas minimum mutlak (*lower-bound floor*) untuk mendeteksi karbohidrat kosong seperti mi instan atau roti putih biasa.
