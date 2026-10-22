# UTS Machine Learning – Linear & Logistic Regression

| | |
|---|---|
| **Nama** | M. Jabbarul Haq |
| **NIM** | 241011400606 |
| **Kelas** | Reg B |
| **random_state** | 6 (2 digit terakhir NIM) |

## Isi Repositori
- `tugas_UTS.ipynb` – notebook lengkap (sudah dijalankan beserta output dan analisis)
- `Ads_Data.csv` – dataset biaya iklan vs penjualan (40 data)
- `Email_Data.csv` – dataset email spam (60 data)

Semua model dan metrik diimplementasikan sendiri dengan NumPy. scikit-learn hanya dipakai pada soal bonus.

## Ringkasan Hasil

### Bagian A – Linear Regression (`Ads_Data.csv`, split 80:20)
- Persamaan (normal equation): **ŷ = 29,4465 + 9,0602 · X**. Setiap tambahan biaya iklan 1 juta Rp menaikkan penjualan sekitar 9,06 juta Rp.

| Data | MAE | MSE | RMSE | R² |
|---|---|---|---|---|
| Training | 4,0854 | 26,9360 | 5,1900 | 0,9516 |
| Testing | 6,0650 | 77,2388 | 8,7886 | 0,9171 |

- Gradient descent (5000 iterasi): lr 0,001 terlalu lambat (b = 25,67; m = 9,66), lr 0,02 sama dengan normal equation, lr 0,1 divergen (`nan`, overflow).
- Prediksi: 4,5 juta → 70,22; 7 juta → 92,87; 12 juta → 138,17 (ekstrapolasi, kurang dapat dipercaya).

### Bagian B – Logistic Regression (`Email_Data.csv`, split 75:25)
- Persamaan: **P(Spam) = σ(−9,5523 + 0,8454 · JumlahLink + 0,8687 · KataPromo)**
- Data testing (threshold 0,5): accuracy **0,9333**, precision 0,8000, recall 1,0000, F1 0,8889 (TN = 10, FP = 1, FN = 0, TP = 4).
- Decision boundary: KataPromo = 10,996 − 0,9731 · JumlahLink. 1 dari 15 data testing salah klasifikasi.
- Threshold dipilih **0,7** (false positive lebih merugikan pengguna).
- Prediksi email baru: E1 Bukan Spam, E2 Bukan Spam, E3 Spam, E4 Spam.

### Bagian C & Bonus
- Jawaban konsep C1–C5 ada di notebook.
- Bonus: Linear Regression scikit-learn identik dengan implementasi sendiri. Logistic Regression berbeda karena scikit-learn memakai regularisasi L2 secara default (C = 1); dengan C = 1e10 hasilnya mendekati implementasi sendiri.
