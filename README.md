# Prediksi Nilai Tukar Mata Uang SAR terhadap IDR Menggunakan GRU📈

Project ini bertujuan untuk memprediksi nilai tukar mata uang Saudi Riyal (SAR) terhadap Rupiah Indonesia (IDR) menggunakan metode **Gated Recurrent Unit (GRU)**. Model ini digunakan untuk mempelajari pola historis kurs dan menghasilkan prediksi nilai kurs berdasarkan data sebelumnya.

Dataset yang digunakan berasal dari **Bank Indonesia**, dengan fokus pada data **Kurs Beli SAR terhadap IDR**.

## 📌Deskripsi Project

Nilai tukar mata uang merupakan salah satu indikator ekonomi yang bersifat fluktuatif dan berubah dari waktu ke waktu. Dalam project ini, data historis kurs SAR terhadap IDR digunakan sebagai data time series untuk membangun model prediksi berbasis deep learning.

Model yang digunakan adalah **GRU (Gated Recurrent Unit)**, yaitu salah satu arsitektur Recurrent Neural Network (RNN) yang cocok digunakan untuk pemodelan data berurutan seperti data kurs, harga saham, cuaca, dan data time series lainnya.

## 📂Dataset

Dataset yang digunakan merupakan data kurs transaksi SAR terhadap IDR yang bersumber dari **Bank Indonesia**.
Link dataset:

https://www.bi.go.id/id/statistik/informasi-kurs/transaksi-bi/default.aspx

Informasi dataset:

- Sumber data: Bank Indonesia
- Mata uang: Saudi Riyal (SAR)
- Target prediksi: Kurs Beli SAR terhadap IDR
- Periode data: Januari 2022 sampai Juni 2025
- Jumlah data: 832 baris
- Kolom utama:
  - `Tanggal`
  - `Kurs Beli`

## ⚙️Metode

Tahapan yang dilakukan dalam project ini meliputi:

1. Mengambil data historis kurs SAR terhadap IDR dari Bank Indonesia
2. Melakukan preprocessing data
3. Mengubah kolom tanggal ke format datetime
4. Mengurutkan data berdasarkan tanggal
5. Melakukan eksplorasi data awal
6. Melakukan normalisasi data menggunakan MinMaxScaler
7. Membagi data menjadi data training, validation, dan testing
8. Membentuk data sequence untuk input model GRU
9. Membangun model GRU
10. Melakukan training model
11. Mengevaluasi performa model
12. Membandingkan hasil prediksi dengan data aktual

## Pembagian Data

Data dibagi menjadi tiga subset:

| Subset | Jumlah Data |
|---|---:|
| Training | 665 |
| Validation | 83 |
| Testing | 84 |

Pembagian data dilakukan secara kronologis agar sesuai dengan karakteristik data time series.

## Arsitektur Model

Model GRU yang digunakan terdiri dari beberapa layer GRU dan satu layer linear sebagai output.

Konfigurasi model terbaik:

| Komponen | Nilai |
|---|---|
| Lookback | 6 |
| Batch Size | 16 |
| Learning Rate | 0.001 |
| Hidden Sizes | 256, 128, 64 |
| Max Epoch | 100 |
| Early Stopping Patience | 10 |

Ringkasan arsitektur model:

| Layer | Output Shape | Jumlah Parameter |
|---|---:|---:|
| GRU Layer 1 | `(None, 6, 256)` | 198,912 |
| GRU Layer 2 | `(None, 6, 128)` | 148,224 |
| GRU Layer 3 | `(None, 64)` | 37,248 |
| Linear Layer | `(None, 1)` | 65 |
| **Total** | - | **384,449** |

## Evaluasi Model

Model terbaik diperoleh pada:

| Metrik | Nilai |
|---|---:|
| Run ID | 002 |
| Validation Loss terbaik | 0.000599 |
| Epoch terbaik | 43 |
| Validation RMSE | 0.024482 |

Hasil evaluasi pada data uji:

| Metrik | Nilai |
|---|---:|
| RMSE skala normalisasi | 0.030005 |
| RMSE denormalisasi | 17.478765 |
| MAPE denormalisasi | 0.2970% |

Berdasarkan nilai MAPE yang rendah, model GRU mampu menghasilkan prediksi kurs SAR terhadap IDR dengan tingkat kesalahan relatif kecil pada data uji.

## Contoh Hasil Prediksi

Beberapa contoh perbandingan nilai aktual dan hasil prediksi:

| Tanggal | Kurs Aktual | Kurs Prediksi |
|---|---:|---:|
| 2025-02-19 | 4317.73 | 4301.05 |
| 2025-02-20 | 4339.48 | 4325.46 |
| 2025-02-21 | 4335.91 | 4341.76 |
| 2025-02-24 | 4324.70 | 4332.74 |
| 2025-02-25 | 4325.50 | 4323.59 |

Contoh hasil akhir prediksi:

| Tanggal | Kurs Aktual | Kurs Prediksi |
|---|---:|---:|
| 2025-06-23 | 4347.61 | 4345.25 |
| 2025-06-24 | 4371.07 | 4346.45 |
| 2025-06-25 | 4341.54 | 4375.64 |
| 2025-06-26 | 4322.12 | 4329.51 |
| 2025-06-30 | 4306.58 | 4324.70 |

## Tools dan Library

Project ini menggunakan beberapa tools dan library berikut:

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- PyTorch

## File Project

Repository ini hanya berisi satu file utama:

```text
Prediksi Nilai Tukar Mata Uang SAR–IDR.ipynb
```

File notebook tersebut berisi seluruh proses mulai dari preprocessing, normalisasi data, pembuatan model GRU, training, evaluasi, hingga visualisasi hasil prediksi.


## Kesimpulan

Project ini menunjukkan penerapan model GRU untuk prediksi nilai tukar mata uang SAR terhadap IDR. Berdasarkan hasil evaluasi, model mampu menghasilkan prediksi yang cukup baik dengan nilai MAPE sebesar **0.2970%** pada data uji.

Model ini dapat dikembangkan lebih lanjut dengan menambahkan variabel eksternal seperti inflasi, suku bunga, harga minyak dunia, atau indikator ekonomi lainnya agar hasil prediksi menjadi lebih komprehensif.

## Catatan

Dataset berasal dari Bank Indonesia dan digunakan untuk keperluan pembelajaran serta penelitian akademik.
