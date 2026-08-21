# Penerapan Metode Interpolasi Inverse Distance Weighted menggunakan Quantum GIS (Studi Kasus: Papua Barat dan Barat Daya)

Repository ini merupakan dokumentasi pendamping tugas akhir yang membahas penerapan metode interpolasi **Inverse Distance Weighted (IDW)** menggunakan **Quantum GIS (QGIS)** untuk memetakan distribusi spasial curah hujan di wilayah **Papua Barat dan Papua Barat Daya**.

Penelitian menggunakan data curah hujan dari lima stasiun pengamatan BMKG, yaitu Manokwari Selatan, Meteorologi Rendani, Meteorologi Seigun, Meteorologi Torea, dan Meteorologi Utarom. Analisis dilakukan untuk bulan Oktober tahun 2020 dan Oktober tahun 2025.

Hasil utama penelitian berupa peta distribusi spasial curah hujan hasil interpolasi IDW, garis kontur, serta perbandingan pola distribusi curah hujan antara Oktober 2020 dan Oktober 2025.

---

## Tujuan Penelitian

Penelitian ini bertujuan untuk:

1. Menerapkan metode interpolasi **Inverse Distance Weighted (IDW)** menggunakan Quantum GIS terhadap data curah hujan dari lima stasiun pengamatan di wilayah Papua Barat dan Papua Barat Daya.
2. Menghasilkan dan menganalisis peta distribusi spasial curah hujan hasil interpolasi IDW pada bulan Oktober tahun 2020 dan Oktober tahun 2025.
3. Menganalisis perbedaan pola distribusi spasial curah hujan hasil interpolasi antara bulan Oktober tahun 2020 dan Oktober tahun 2025.

---

## Area Penelitian

Wilayah penelitian mencakup Provinsi Papua Barat dan Papua Barat Daya sesuai dengan batas wilayah administratif yang digunakan dalam penelitian.

### Peta Area Penelitian

<img width="868" height="671" alt="image" src="https://github.com/user-attachments/assets/6962abc6-30a0-4022-857d-63d88ac18f8f" />

*Gambar 1. Peta area penelitian dan lokasi stasiun pengamatan curah hujan.*

Lima stasiun pengamatan yang digunakan sebagai titik input interpolasi adalah:

| No. | Stasiun | Lintang | Bujur | Elevasi |
|---|---|---:|---:|---:|
| 1 | Manokwari Selatan | -1.47000 | 134.19000 | 20 m |
| 2 | Meteorologi Rendani | -0.89227 | 134.05041 | 3 m |
| 3 | Meteorologi Seigun | -0.89118 | 131.28575 | 0 m |
| 4 | Meteorologi Torea | -2.91938 | 132.26496 | 126 m |
| 5 | Meteorologi Utarom | -3.64333 | 133.69694 | 5 m |

Sumber data stasiun: **Badan Meteorologi, Klimatologi, dan Geofisika (BMKG)**.

---

## Data

Data utama penelitian berupa data curah hujan bulanan pada bulan Oktober tahun 2020 dan Oktober tahun 2025.

| Dataset | Sumber | Periode | Fungsi |
|---|---|---|---|
| Data curah hujan stasiun | BMKG | Oktober 2020 | Input interpolasi IDW |
| Data curah hujan stasiun | BMKG | Oktober 2025 | Input interpolasi IDW |
| Lokasi stasiun | BMKG | Sesuai penelitian | Titik pengamatan |
| Batas administrasi | Data spasial penelitian | Sesuai wilayah penelitian | Batas area analisis |

Data titik digunakan sebagai input untuk menghasilkan estimasi nilai curah hujan pada lokasi yang tidak memiliki pengamatan langsung.

Nilai hasil interpolasi pada lokasi tanpa stasiun pengamatan merupakan **nilai estimasi berdasarkan metode IDW**, bukan hasil pengukuran langsung di lapangan.

---

## Metodologi

Tahapan penelitian secara umum adalah sebagai berikut:

1. Pengumpulan data curah hujan dari stasiun pengamatan BMKG.
2. Pengumpulan data lokasi stasiun dan batas wilayah penelitian.
3. Pemeriksaan dan persiapan data spasial.
4. Pengolahan data titik stasiun di QGIS.
5. Penerapan metode interpolasi **Inverse Distance Weighted (IDW)**.
6. Pembuatan raster hasil interpolasi.
7. Pembuatan garis kontur curah hujan.
8. Visualisasi hasil dalam bentuk peta.
9. Analisis distribusi spasial curah hujan.
10. Perbandingan hasil interpolasi Oktober 2020 dan Oktober 2025.
11. Validasi pola spasial dengan informasi curah hujan dari BMKG.
12. Interpretasi hasil penelitian.

Dokumentasi metodologi lengkap dapat dilihat pada [`docs/methodology.md`](docs/methodology.md).

Petunjuk reproduksi lengkap tersedia pada [`docs/reproduction.md`](docs/reproduction.md).

Keterbatasan penelitian dijelaskan pada [`docs/limitations.md`](docs/limitations.md).

---

## Metode Interpolasi IDW

Inverse Distance Weighted (IDW) digunakan untuk memperkirakan nilai pada lokasi yang tidak memiliki data pengamatan langsung berdasarkan nilai dari titik-titik pengamatan di sekitarnya.

Prinsip utama IDW adalah bahwa titik pengamatan yang memiliki jarak lebih dekat terhadap lokasi estimasi memiliki pengaruh yang lebih besar dibandingkan titik yang lebih jauh.

Secara umum, estimasi IDW dapat dituliskan sebagai:

\[
Z(x)=\frac{\sum_{i=1}^{n} Z_i d_i^{-p}}
{\sum_{i=1}^{n} d_i^{-p}}
\]

Keterangan:

- `Z(x)` = nilai estimasi pada lokasi yang tidak diketahui
- `Zi` = nilai pengamatan pada titik ke-i
- `di` = jarak antara lokasi estimasi dengan titik pengamatan ke-i
- `p` = power IDW
- `n` = jumlah titik pengamatan

---

## Parameter Analisis

Parameter utama yang digunakan dalam proses interpolasi adalah:

| Parameter | Nilai |
|---|---|
| Metode | Inverse Distance Weighted (IDW) |
| Power | 2 |
| CRS | EPSG:4326 – WGS 84 |
| Ukuran pixel X | 0.009263 |
| Ukuran pixel Y | 0.009263 |
| Perangkat lunak | QGIS 3.38.0-Grenoble |
| Periode analisis | Oktober 2020 dan Oktober 2025 |
| Jumlah stasiun | 5 |

Parameter tersebut digunakan dalam proses pengolahan data spasial menggunakan QGIS.

---

## Hasil Penelitian

### Distribusi Curah Hujan Oktober 2020

Hasil interpolasi IDW digunakan untuk menggambarkan distribusi spasial curah hujan pada bulan Oktober 2020 di wilayah Papua Barat dan Papua Barat Daya.

Zona hasil interpolasi menunjukkan variasi nilai curah hujan berdasarkan nilai pada lima stasiun pengamatan dan pengaruh jarak antar titik.

<img width="757" height="506" alt="image" src="https://github.com/user-attachments/assets/862aa824-a4ea-4cd6-825b-de2b5b9b63a2" />

*Gambar 2. Hasil interpolasi IDW distribusi curah hujan bulan Oktober 2020.*

> **Catatan:** Nilai pada area yang tidak memiliki stasiun pengamatan merupakan hasil estimasi interpolasi IDW.

---

### Distribusi Curah Hujan Oktober 2025

Hasil interpolasi IDW juga diterapkan pada data bulan Oktober 2025 untuk memperoleh gambaran distribusi spasial curah hujan.

Peta hasil interpolasi digunakan untuk melihat pola persebaran curah hujan dan membandingkannya dengan kondisi pada Oktober 2020.

<img width="796" height="563" alt="image" src="https://github.com/user-attachments/assets/b8aa9284-4a2e-4854-a6ea-1f81b848dd0c" />

*Gambar 3. Hasil interpolasi IDW distribusi curah hujan bulan Oktober 2025.*

---

## Perbandingan Oktober 2020 dan Oktober 2025

Berdasarkan hasil penelitian, rata-rata curah hujan dari lima stasiun pengamatan mengalami perubahan antara kedua periode.

| Tahun | Rata-rata curah hujan |
|---|---:|
| Oktober 2020 | 243,0 mm |
| Oktober 2025 | 331,3 mm |
| Perubahan | +88,3 mm |

Secara rata-rata, curah hujan pada Oktober 2025 lebih tinggi dibandingkan Oktober 2020.

Namun, perubahan tersebut tidak terjadi secara seragam pada seluruh wilayah penelitian. Perbedaan pola spasial perlu dipahami sebagai perbandingan antara dua periode pengamatan dan **tidak secara langsung menunjukkan tren perubahan curah hujan jangka panjang**.

---

## Validasi

Validasi dilakukan secara kualitatif dengan membandingkan pola hasil interpolasi IDW dengan informasi curah hujan dari BMKG untuk periode Oktober 2020 dan Oktober 2025.

Validasi digunakan untuk melihat kesesuaian pola spasial hasil interpolasi dengan kondisi data pengamatan yang tersedia. Validasi ini tidak dimaksudkan sebagai pengukuran akurasi numerik menggunakan MAE, RMSE, atau metode *cross-validation*.

Hasil interpolasi tetap harus dipahami sebagai estimasi spasial karena jumlah dan persebaran stasiun pengamatan yang digunakan dalam penelitian relatif terbatas.

---

## Keterbatasan Penelitian

Penelitian memiliki beberapa keterbatasan:

- Jumlah stasiun pengamatan yang digunakan hanya lima titik.
- Sebaran stasiun belum sepenuhnya merata di seluruh wilayah penelitian.
- Periode yang dibandingkan hanya Oktober 2020 dan Oktober 2025.
- Nilai pada lokasi tanpa stasiun merupakan hasil estimasi interpolasi.
- Hasil penelitian tidak dimaksudkan sebagai pemodelan khusus risiko banjir, kekeringan, atau longsor.
- Penelitian tidak dapat digunakan untuk menyimpulkan tren perubahan curah hujan jangka panjang hanya berdasarkan dua periode pengamatan.

---

## Cara Mereproduksi Analisis
Untuk mereproduksi penelitian:
1. Install QGIS 3.38.0-Grenoble atau versi yang kompatibel.
2. Siapkan data curah hujan dan koordinat lima stasiun pengamatan.
3. Masukkan data titik stasiun ke dalam QGIS.
4. Pastikan CRS data sesuai dengan konfigurasi penelitian.
5. Jalankan proses interpolasi menggunakan algoritma IDW.
6. Gunakan parameter IDW yang telah dicantumkan pada bagian Parameter Analisis.
7. Simpan hasil interpolasi sebagai raster.
8. Buat garis kontur dari raster hasil interpolasi.
9. Lakukan visualisasi peta.
10. Ulangi proses untuk data Oktober 2020 dan Oktober 2025.
11. Bandingkan hasil kedua periode.
12. Simpan hasil akhir pada folder outputs.

---

## Sumber Data dan Acknowledgement

Data pengamatan curah hujan yang digunakan dalam penelitian bersumber dari:

**Badan Meteorologi, Klimatologi, dan Geofisika (BMKG).**

Repository ini dibuat sebagai dokumentasi akademik pendamping tugas akhir dan tidak menggantikan laporan tugas akhir secara keseluruhan.

Penggunaan kembali data pihak ketiga harus mengikuti ketentuan dan hak penggunaan dari pemilik data.

---

Author

Firman Panggala

NIM: 1212002024

Universitas Bakrie

Program Studi Informatika

Tahun: 2026

---

## Citation

Jika menggunakan repository ini sebagai referensi, silakan mengutip:

> Panggala, Firman. (2026). Penerapan Metode Interpolasi Inverse Distance Weighted (IDW) Menggunakan Quantum GIS (Studi Kasus Papua Barat dan Barat Daya). Universitas Bakrie.

---

## License

Dokumentasi dan materi penelitian yang dibuat secara mandiri dalam repository ini dapat digunakan sesuai dengan lisensi repository.

Data yang berasal dari pihak ketiga, termasuk data BMKG, tetap mengikuti ketentuan penggunaan dan hak dari sumber data tersebut. Repository ini tidak memberikan lisensi ulang terhadap data pihak ketiga.

---

## Disclaimer

Hasil interpolasi pada wilayah yang tidak memiliki stasiun pengamatan merupakan hasil estimasi menggunakan metode IDW. Hasil tersebut tidak dapat dianggap sebagai hasil pengukuran langsung di lapangan.

Repository ini dibuat untuk keperluan dokumentasi dan reproduksi penelitian akademik.

