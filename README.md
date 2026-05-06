# Wetland Buffer Effect PINN vs NN

Project ini berisi notebook untuk simulasi efek buffer termal lahan basah menggunakan data dummy berbasis persamaan heat diffusion, lalu membandingkan prediksi Neural Network biasa dan Physics-Informed Neural Network.

## Isi Notebook

File utama: `wetland_buffer_pinn_nn.ipynb`

Notebook mencakup:

- Turunan persamaan heat diffusion dari Hukum I Termodinamika dan Hukum Fourier.
- Penjelasan teori fisika pendukung efek buffer lahan basah, seperti kapasitas panas air, evapotranspirasi, penyimpanan panas tanah basah, dan difusi panas.
- Pembuatan data dummy realistis untuk 3 hari observasi dari 5 AM sampai 7 PM.
- Simulasi benchmark sintetis Day 1 sampai Day 6 dengan asumsi cuaca cerah.
- Training Neural Network dan PINN menggunakan data Day 1 sampai Day 3.
- Evaluasi ekstrapolasi untuk Day 4 sampai Day 6.
- Perbandingan akurasi NN vs PINN menggunakan RMSE, MAE, R2, bias, dan error maksimum.
- Plot 2D suhu lahan basah dan animasi GIF untuk hasil prediksi.

## Struktur Folder

```text
.
├── wetland_buffer_pinn_nn.ipynb
├── README.md
├── LICENSE
├── sample/
│   ├── dummy_observations_train_days_1_3.csv
│   ├── dummy_truth_benchmark_days_1_6.csv
│   └── daily_period_buffer_summary.csv
└── outputs/
    ├── future_extrapolation_metrics.csv
    ├── future_extrapolation_metrics_by_period.csv
    ├── future_predictions_days_4_6.csv
    ├── wetland_buffer_future_animation.gif
    └── *.png
```

## Cara Menjalankan

Jalankan notebook dengan Jupyter:

```bash
jupyter notebook wetland_buffer_pinn_nn.ipynb
```

Atau eksekusi penuh dari terminal:

```bash
jupyter nbconvert --to notebook --execute --inplace wetland_buffer_pinn_nn.ipynb
```

Parameter utama yang mudah diganti tersedia di sel `CONFIG`, termasuk ukuran domain, resolusi grid, periode waktu, parameter fisika, jumlah epoch NN/PINN, dan folder output.

## Output Utama

- `sample/`: data dummy dan ringkasan efek buffer.
- `outputs/future_extrapolation_metrics.csv`: metrik akurasi NN vs PINN untuk Day 4 sampai Day 6.
- `outputs/future_predictions_days_4_6.csv`: hasil prediksi ekstrapolasi.
- `outputs/wetland_buffer_future_animation.gif`: animasi suhu Day 4 sampai Day 6 yang loop kembali ke Day 4.
- `outputs/*.png`: peta suhu, peta error, scatter plot, dan grafik metrik.

## Catatan

Data di project ini adalah data sintetis untuk demonstrasi metode. Untuk analisis lapangan nyata, ganti fungsi cuaca, peta penutup lahan, kondisi awal, dan parameter fisika dengan data sensor atau hasil kalibrasi lokal.

## Lisensi

Project ini dirilis dengan lisensi MIT. Lihat file `LICENSE` untuk detail.
