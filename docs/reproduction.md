# Reproduction Guide

## 1. Requirements

Analisis dilakukan menggunakan:

- QGIS 3.38.0-Grenoble
- Data curah hujan Oktober 2020
- Data curah hujan Oktober 2025
- Data koordinat lima stasiun pengamatan
- Data batas wilayah penelitian

## 2. Input Data

Data penelitian disimpan pada:

```text
data/raw/
data/processed/ 
```
Data yang digunakan mencakup lima stasiun pengamatan:

Manokwari Selatan
Rendani
Seigun
Torea
Utarom

Periode analisis:

Oktober 2020
Oktober 2025

---

3. QGIS Project

Proyek QGIS disimpan pada:
```text
project/
```
Buka file proyek QGIS untuk melihat layer, simbologi, raster, dan konfigurasi analisis yang digunakan dalam penelitian.

---

## 4. Interpolation

Interpolasi dilakukan menggunakan metode **Inverse Distance Weighted (IDW)** pada QGIS.

Metode IDW digunakan untuk memperkirakan nilai curah hujan pada lokasi yang tidak memiliki stasiun pengamatan berdasarkan nilai dari titik pengamatan di sekitarnya. Titik yang memiliki jarak lebih dekat memberikan pengaruh yang lebih besar terhadap nilai hasil interpolasi.

Interpolasi dilakukan secara terpisah untuk dua periode:

- Oktober 2020
- Oktober 2025

### Parameter IDW

| Parameter | Nilai |
|---|---|
| Metode | Inverse Distance Weighted (IDW) |
| Power | 2 |
| Jumlah stasiun | 5 |
| CRS | EPSG:4326 – WGS 84 |
| Pixel size X | 0.009263 |
| Pixel size Y | 0.009263 |

Lima stasiun yang digunakan sebagai titik input adalah:

1. Manokwari Selatan
2. Rendani
3. Seigun
4. Torea
5. Utarom

### Proses Interpolasi

Secara umum, proses interpolasi dilakukan dengan urutan:

```text
Data curah hujan
        ↓
Data titik stasiun
        ↓
Input nilai curah hujan
        ↓
Interpolasi IDW
        ↓
Raster hasil interpolasi
```

Hasil proses interpolasi berupa raster yang menggambarkan estimasi distribusi spasial curah hujan pada wilayah penelitian.

---

## 5. Processing Workflow

Setelah proses interpolasi IDW selesai, hasil raster diolah lebih lanjut untuk menghasilkan peta distribusi curah hujan yang sesuai dengan wilayah penelitian.

Tahapan pengolahan dilakukan dengan urutan sebagai berikut:

```text
Data curah hujan
        ↓
Data titik stasiun
        ↓
Interpolasi IDW
        ↓
Raster hasil interpolasi
        ↓
Clip raster berdasarkan wilayah penelitian
        ↓
Pengolahan raster
        ↓
Pembuatan kontur/isohyet
        ↓
Visualisasi dan layout peta
        ↓
Analisis hasil
```

### 5.1 Clip Raster

Raster hasil interpolasi dipotong menggunakan batas wilayah penelitian.

Tujuan proses ini adalah membatasi hasil interpolasi agar hanya mencakup wilayah Papua Barat dan Barat Daya yang menjadi area penelitian.

Hasil proses ini disimpan sebagai raster hasil clipping dan digunakan pada tahapan pengolahan serta visualisasi berikutnya.

### 5.2 Pengolahan Raster

Raster hasil interpolasi kemudian diolah untuk mendukung visualisasi distribusi curah hujan.

Pengolahan raster dilakukan menggunakan tools yang tersedia pada QGIS, termasuk **Rasterize** dan **Raster Calculator** sesuai tahapan pengolahan dalam penelitian.

Tahapan ini digunakan untuk menghasilkan data raster yang dapat digunakan dalam pembuatan peta distribusi curah hujan.

### 5.3 Pembuatan Kontur

Garis kontur curah hujan atau **isohyet** dibuat berdasarkan raster hasil interpolasi.

Kontur digunakan untuk menunjukkan garis yang menghubungkan lokasi dengan nilai curah hujan yang sama sehingga pola distribusi spasial curah hujan dapat lebih mudah diamati.

Hasil kontur disimpan dalam format data vektor dan digunakan sebagai salah satu komponen pada peta hasil penelitian.

### 5.4 Layout Peta

Hasil raster interpolasi, kontur, titik stasiun, dan batas wilayah kemudian disusun dalam layout peta menggunakan QGIS.

Layout peta mencakup:

- judul peta;
- legenda;
- skala;
- arah utara;
- informasi stasiun pengamatan;
- batas wilayah penelitian;
- hasil interpolasi;
- dan kontur curah hujan.

Peta akhir digunakan untuk menampilkan pola distribusi spasial curah hujan pada wilayah penelitian.

### 5.5 Perbandingan Hasil

Proses pengolahan dilakukan untuk data Oktober 2020 dan Oktober 2025.

Kedua hasil kemudian dibandingkan berdasarkan:

- distribusi spasial curah hujan;
- nilai curah hujan pada stasiun pengamatan;
- rentang nilai hasil interpolasi;
- dan pola garis kontur.

Perbandingan digunakan untuk melihat perbedaan distribusi curah hujan antara kedua periode penelitian.

---

## 6. Outputs

Hasil pengolahan penelitian disimpan berdasarkan jenis output agar data, hasil analisis, dan visualisasi dapat dibedakan dengan jelas.

Struktur output pada repository adalah:

```text
outputs/
├── maps/
├── raster/
├── vector/
└── tables/
```

### 6.1 Maps

Folder:

```text
outputs/maps/
```

digunakan untuk menyimpan hasil visualisasi peta penelitian dalam format gambar.

Output yang dapat disimpan pada folder ini meliputi:

- peta area penelitian;
- peta distribusi curah hujan Oktober 2020;
- peta distribusi curah hujan Oktober 2025;
- peta hasil interpolasi IDW;
- dan peta hasil analisis lainnya.

Peta digunakan untuk memvisualisasikan pola distribusi spasial curah hujan pada wilayah penelitian.

### 6.2 Raster

Folder:

```text
outputs/raster/
```

digunakan untuk menyimpan hasil interpolasi dan pengolahan raster.

File raster yang dihasilkan dari proses IDW dan proses clipping wilayah penelitian disimpan dalam format:

```text
.tif
```

Raster merupakan hasil utama proses interpolasi dan digunakan sebagai dasar pembuatan visualisasi serta kontur curah hujan.

### 6.3 Vector

Folder:

```text
outputs/vector/
```

digunakan untuk menyimpan data vektor hasil pengolahan spasial.

Salah satu output utama adalah garis kontur curah hujan atau isohyet yang dihasilkan dari raster hasil interpolasi.

Format data vektor yang digunakan dalam penelitian dapat berupa:

```text
.gpkg
```

### 6.4 Tables

Folder:

```text
outputs/tables/
```

digunakan untuk menyimpan tabel hasil pengolahan dan analisis.

Tabel dapat mencakup:

- rekapitulasi hasil analisis;
- perbandingan curah hujan Oktober 2020 dan Oktober 2025;
- nilai hasil pengolahan;
- dan tabel pendukung interpretasi hasil penelitian.

Format tabel yang digunakan dapat berupa:

```text
.csv
.xlsx
```

### 6.5 Hubungan Output dengan Tahapan Analisis

Hubungan antara proses pengolahan dan output penelitian dapat diringkas sebagai berikut:

```text
Interpolasi IDW
       ↓
Raster hasil interpolasi
       ↓
outputs/raster/

Raster hasil interpolasi
       ↓
Pembuatan kontur
       ↓
outputs/vector/

Raster + kontur + stasiun + batas wilayah
       ↓
Layout peta
       ↓
outputs/maps/

Hasil pengolahan dan analisis
       ↓
Tabel hasil
       ↓
outputs/tables/
```

Output pada repository digunakan untuk mendokumentasikan hasil penelitian dan memudahkan pemeriksaan kembali terhadap proses serta hasil analisis.

---

## 7. Reproduction Notes

Repository ini disusun agar tahapan pengolahan data dan hasil penelitian dapat ditelusuri kembali dari data input hingga output.

Untuk mereproduksi analisis, ikuti urutan berikut:

### 7.1 Menyiapkan Data

Siapkan data penelitian yang terdapat pada:

```text
data/raw/
data/processed/
```

Data yang digunakan mencakup data curah hujan Oktober 2020 dan Oktober 2025 serta data spasial pendukung penelitian.

### 7.2 Membuka Proyek QGIS

Buka proyek QGIS yang terdapat pada:

```text
project/
```

Proyek digunakan untuk melihat layer, data spasial, pengaturan simbologi, hasil interpolasi, dan tahapan pengolahan yang digunakan dalam penelitian.

### 7.3 Menjalankan Interpolasi

Gunakan data titik lima stasiun pengamatan sebagai input interpolasi:

1. Manokwari Selatan
2. Rendani
3. Seigun
4. Torea
5. Utarom

Gunakan metode:

```text
Inverse Distance Weighted (IDW)
```

dengan parameter utama:

```text
Power = 2
CRS = EPSG:4326
Pixel size X = 0.009263
Pixel size Y = 0.009263
```

Interpolasi dilakukan untuk masing-masing periode pengamatan.

### 7.4 Mengolah Hasil Interpolasi

Setelah raster hasil interpolasi diperoleh, lakukan tahapan pengolahan sesuai proyek penelitian:

```text
Raster interpolasi
        ↓
Clip berdasarkan wilayah penelitian
        ↓
Pengolahan raster
        ↓
Pembuatan kontur/isohyet
```

### 7.5 Menghasilkan Peta

Gabungkan hasil raster, kontur, titik stasiun, dan batas wilayah dalam layout QGIS.

Hasil layout kemudian diekspor sebagai gambar dan disimpan pada:

```text
outputs/maps/
```

### 7.6 Menyimpan Hasil

Simpan hasil pengolahan berdasarkan jenisnya:

```text
outputs/
├── maps/
├── raster/
├── vector/
└── tables/
```

Dengan demikian:

- hasil peta → `outputs/maps/`
- raster interpolasi → `outputs/raster/`
- kontur/isohyet → `outputs/vector/`
- tabel hasil analisis → `outputs/tables/`

### 7.7 Konsistensi Hasil

Hasil reproduksi dapat berbeda apabila terdapat perbedaan pada:

- data input;
- koordinat stasiun;
- sistem koordinat;
- parameter interpolasi;
- versi QGIS;
- data batas wilayah;
- atau konfigurasi proyek.

Oleh karena itu, reproduksi sebaiknya menggunakan data dan parameter yang tersedia pada repository serta proyek QGIS penelitian.

### 7.8 Parameter yang Tidak Didokumentasikan

Nilai parameter yang tidak tercantum secara jelas dalam tugas akhir tidak diasumsikan dalam dokumentasi ini.

Khususnya, nilai **search radius/jumlah tetangga IDW** perlu diperiksa langsung pada konfigurasi proyek QGIS apabila diperlukan untuk reproduksi secara identik.

Repository ini membedakan antara parameter yang terdokumentasi dalam tugas akhir dan parameter yang belum tersedia secara eksplisit.

---

## 8. Limitations

Reproduksi hasil penelitian memiliki beberapa keterbatasan yang perlu diperhatikan.

### 8.1 Jumlah dan Sebaran Stasiun

Penelitian menggunakan lima stasiun pengamatan, yaitu:

- Manokwari Selatan
- Rendani
- Seigun
- Torea
- Utarom

Sebaran stasiun pengamatan belum merata di seluruh wilayah penelitian. Kondisi ini dapat memengaruhi hasil interpolasi, terutama pada wilayah yang memiliki jarak relatif jauh dari titik pengamatan.

### 8.2 Nilai Hasil Interpolasi

Nilai curah hujan pada lokasi yang tidak memiliki stasiun pengamatan merupakan nilai estimasi yang diperoleh melalui metode IDW.

Oleh karena itu, nilai hasil interpolasi tidak dapat dianggap sebagai hasil pengukuran langsung pada lokasi tersebut.

### 8.3 Periode Data

Analisis dalam penelitian ini menggunakan data curah hujan bulan Oktober tahun 2020 dan 2025.

Perbandingan kedua periode tersebut digunakan untuk melihat perbedaan pola distribusi spasial curah hujan. Hasil perbandingan tidak digunakan untuk menyimpulkan tren perubahan curah hujan jangka panjang.

### 8.4 Keterbatasan Metode IDW

IDW menentukan pengaruh suatu titik berdasarkan jaraknya terhadap lokasi yang diprediksi. Titik yang lebih dekat memiliki pengaruh lebih besar dibandingkan titik yang lebih jauh.

Karena itu, hasil interpolasi dapat dipengaruhi oleh distribusi dan kepadatan titik pengamatan.

### 8.5 Validasi

Validasi penelitian menggunakan data pengamatan yang tersedia pada stasiun penelitian dan membandingkannya dengan pola hasil interpolasi.

Penelitian ini tidak menggunakan jaringan stasiun validasi independen yang terpisah dari data input.

### 8.6 Parameter yang Belum Terdokumentasi

Tidak semua konfigurasi teknis proses interpolasi terdokumentasi secara eksplisit dalam tugas akhir.

Nilai **search radius** atau jumlah tetangga yang digunakan dalam proses IDW tidak dicantumkan apabila tidak tersedia dalam dokumentasi penelitian.

Nilai tersebut tidak diasumsikan dalam repository dan dapat diperiksa melalui konfigurasi proyek QGIS apabila diperlukan.

### 8.7 Data Spasial Pendukung

Hasil reproduksi juga dapat dipengaruhi oleh data batas wilayah dan data spasial pendukung yang digunakan.

Perubahan sumber data, versi data, atau konfigurasi layer dapat menyebabkan perbedaan pada hasil visualisasi maupun batas area analisis.

### 8.8 Interpretasi Hasil

Hasil penelitian digunakan untuk menggambarkan dan membandingkan distribusi spasial curah hujan berdasarkan data dan metode yang digunakan.

Interpretasi hasil perlu mempertimbangkan keterbatasan jumlah stasiun, sebaran titik pengamatan, periode data, serta karakteristik metode IDW.

---

