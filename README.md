# Random Forest

Random Forest mulai banyak digunakan sejak pertama kali diperkenalkan oleh **Leo Breiman (2001)** dan terbukti memiliki beberapa keunggulan:  
- Dapat mengatasi masalah **overfitting**.  
- Tidak sensitif terhadap **pencilan**.  
- Menghasilkan akurasi yang baik.  
- Mampu menangani data tidak seimbang dalam jumlah besar dengan performa yang baik dan waktu eksekusi yang cepat.  

Random Forest adalah salah satu metode ensemble, yaitu metode untuk meningkatkan akurasi analisis klasifikasi. Metode ini membangun beberapa pengklasifikasi dasar (single classifiers) dari data latih dan melakukan agregasi dengan **voting terbanyak** untuk menentukan hasil prediksi akhir.  

Random Forest menggunakan **metode bagging** dan **random feature selection**. Metode ini dikembangkan dari bagging dengan melakukan pemilihan acak terhadap peubah penjelas untuk mengurangi korelasi antar pohon yang terbentuk. Berikut adalah tahapan klasifikasi menggunakan Random Forest pada gugus data yang terdiri atas **n** amatan dan **p** peubah penjelas:  

---

## Tahapan Klasifikasi
### 1. Tahapan Bootstrap
Bootstrap adalah pengambilan contoh yang disertai pengembalian. Pada tahap ini, ambil sebanyak **n** contoh acak dari data latih.  

### 2. Tahapan Random Feature Subset
Susun pohon berdasarkan data hasil bootstrap sebelumnya. Pada setiap proses pemisahan, pilih **m** peubah penjelas secara acak dimana **m < p**. Selanjutnya, lakukan pemisahan terbaik.  

### 3. Pengulangan
Ulangi langkah 1 dan 2 sebanyak **k** kali sehingga diperoleh **k** pohon.  

### 4. Agregasi
Gabungkan hasil prediksi dari **k** pohon menggunakan **majority vote** (mengambil vote terbanyak) untuk menentukan hasil prediksi akhir.  

---

## Perhitungan Entropi dan Information Gain
Setiap proses pemisahan dalam pembentukan pohon memperhatikan **nilai entropi**, kemudian dihitung nilai **information gain**. Peubah dengan nilai information gain terbesar akan digunakan sebagai partisi atau pemisah terbaik.  
---

## Perhitungan Gini Index
Sebagai alternatif entropi, dapat digunakan **Gini Index** untuk menentukan pemisahan terbaik.  
---

## Pengukuran Kinerja Klasifikasi
**Confusion Matrix** digunakan untuk mengevaluasi performa model. Matriks ini menunjukkan jumlah data yang benar maupun salah diklasifikasikan oleh model berdasarkan data latih:  

|                    | Prediksi Positif | Prediksi Negatif |
|--------------------|------------------|------------------|
| **Kelas Positif**  | True Positive (TP) | False Negative (FN) |
| **Kelas Negatif**  | False Positive (FP) | True Negative (TN)  |

### Ukuran Kinerja
- **Akurasi**: Mengukur seberapa banyak data diklasifikasikan dengan benar.  
- **Sensitivitas**: Proporsi data positif yang diklasifikasikan dengan benar.  
- **Spesifisitas**: Proporsi data negatif yang diklasifikasikan dengan benar.  

### Area Under Curve (AUC)
AUC menggambarkan performa model berdasarkan kurva ROC (**Receiver Operating Characteristic**).  

#### Interpretasi Nilai AUC:
| Nilai AUC | Interpretasi       |
|-----------|--------------------|
| 0.5–0.6   | Sangat Lemah      |
| 0.6–0.7   | Lemah             |
| 0.7–0.8   | Cukup             |
| 0.8–0.9   | Baik              |
| 0.9–1.0   | Sangat Baik       |

---
