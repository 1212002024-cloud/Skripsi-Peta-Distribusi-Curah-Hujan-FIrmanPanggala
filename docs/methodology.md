# Methodology

## 1. Overview

Penelitian ini menerapkan metode interpolasi **Inverse Distance Weighted (IDW)** menggunakan **Quantum GIS (QGIS)** untuk memetakan distribusi spasial curah hujan di wilayah Papua Barat dan Barat Daya.

Analisis menggunakan data curah hujan bulan **Oktober 2020** dan **Oktober 2025** dari lima stasiun pengamatan BMKG, yaitu:

- Manokwari Selatan
- Rendani
- Seigun
- Torea
- Utarom

Hasil utama penelitian berupa raster hasil interpolasi, peta distribusi spasial curah hujan, garis kontur curah hujan (isohyet), serta perbandingan pola distribusi antara Oktober 2020 dan Oktober 2025.

> **Catatan interpretasi:** Nilai pada lokasi yang tidak memiliki stasiun pengamatan merupakan nilai estimasi hasil interpolasi IDW dan bukan hasil pengukuran langsung di lapangan.

---

## 2. Research Area

Wilayah penelitian mencakup Provinsi Papua Barat dan Barat Daya sesuai dengan batas wilayah administratif yang digunakan dalam penelitian.

Lima stasiun pengamatan digunakan sebagai titik input interpolasi:

| Stasiun | Lintang | Bujur | Elevasi |
|---|---:|---:|---:|
| Manokwari Selatan | -1.47000 | 134.19000 | 20 m |
| Rendani | -0.89227 | 134.05041 | 3 m |
| Seigun | -0.89118 | 131.28575 | 0 m |
| Torea | -2.91938 | 132.26496 | 126 m |
| Utarom | -3.64333 | 133.69694 | 5 m |

Kelima stasiun merupakan titik pengamatan yang tersedia dan digunakan sebagai dasar analisis spasial penelitian.

Sebaran stasiun belum merata di seluruh wilayah penelitian. Kondisi tersebut perlu diperhatikan dalam interpretasi karena hasil IDW lebih dipengaruhi oleh titik pengamatan yang memiliki jarak lebih dekat terhadap lokasi yang diestimasi. 

---

## 3. Data Preparation

### 3.1 Data Curah Hujan

Data utama penelitian berupa data curah hujan bulanan dari BMKG untuk:

- Oktober 2020
- Oktober 2025

Data mencakup nilai curah hujan, koordinat lokasi stasiun, dan elevasi.

Elevasi digunakan sebagai informasi karakteristik lokasi stasiun dan **tidak digunakan sebagai variabel pembobot dalam interpolasi IDW**. :contentReference[oaicite:3]{index=3}

### 3.2 Pemeriksaan Data

Sebelum digunakan dalam analisis spasial, data diperiksa berdasarkan:

1. kelengkapan data;
2. kesesuaian nama stasiun;
3. koordinat lintang dan bujur;
4. nilai curah hujan; dan
5. kesesuaian format data.

Data kemudian disusun dalam bentuk tabel sehingga dapat digunakan sebagai atribut pada data spasial titik di QGIS. :contentReference[oaicite:4]{index=4}

### 3.3 Digitasi dan Data Spasial

Data tabel yang berisi koordinat stasiun diubah menjadi data titik dalam format GIS. Data batas wilayah administratif digunakan untuk menentukan cakupan wilayah penelitian.

Data spasial tambahan yang digunakan dalam penelitian meliputi:

- batas administratif dari **Global Administrative Areas (GADM)**;
- data referensi peta dasar dari **OpenStreetMap (OSM)**.

Data tersebut digunakan untuk mendukung proses clipping, visualisasi, dan interpretasi spasial. :contentReference[oaicite:5]{index=5}

---

## 4. Interpolation Method

### 4.1 Inverse Distance Weighted (IDW)

Metode utama yang digunakan adalah **Inverse Distance Weighted (IDW)**.

IDW memperkirakan nilai pada lokasi yang tidak memiliki pengamatan langsung berdasarkan nilai titik pengamatan di sekitarnya. Titik yang memiliki jarak lebih dekat terhadap lokasi estimasi memperoleh pengaruh lebih besar dibandingkan titik yang lebih jauh.

Secara matematis, IDW dinyatakan sebagai:

\[
Z(x_0) =
\frac{
\sum_{i=1}^{n}\frac{Z(x_i)}{d_i^p}
}{
\sum_{i=1}^{n}\frac{1}{d_i^p}
}
\]

Keterangan:

- `Z(x₀)` = nilai curah hujan hasil interpolasi pada lokasi yang diprediksi;
- `Z(xᵢ)` = nilai curah hujan pada titik pengamatan ke-i;
- `dᵢ` = jarak antara lokasi prediksi dengan titik pengamatan ke-i;
- `p` = parameter pangkat (*power*);
- `n` = jumlah titik pengamatan.

Dalam penelitian ini, perhitungan interpolasi dilakukan menggunakan QGIS. :contentReference[oaicite:6]{index=6}

---

## 5. IDW Parameters

Parameter utama yang digunakan dalam proses interpolasi adalah:

| Parameter | Nilai |
|---|---|
| Metode | Inverse Distance Weighted (IDW) |
| Power (P) | 2 |
| Jumlah stasiun | 5 stasiun pengamatan |
| Pixel size X | 0.009263 |
| Pixel size Y | 0.009263 |
| CRS | EPSG:4326 – WGS 84 |
| Software | QGIS 3.38.0-Grenoble |

Pengaturan tersebut digunakan secara konsisten untuk interpolasi data curah hujan Oktober 2020 dan Oktober 2025. :contentReference[oaicite:7]{index=7}

> **Catatan:** Nilai *search radius* dan jumlah tetangga tidak dicantumkan di sini karena nilai aktualnya tidak tercantum pada Tabel 4.1 tugas akhir. Parameter tersebut tidak akan diasumsikan tanpa pemeriksaan terhadap konfigurasi proyek QGIS.

---

## 6. Analysis Workflow

Proses analisis dilakukan melalui tahapan berikut:

### Step 1 — Identifikasi Masalah

Penelitian diawali dengan identifikasi masalah distribusi curah hujan di Papua Barat dan Barat Daya, terutama keterbatasan jumlah dan ketidakmerataan titik pengamatan.

### Step 2 — Studi Literatur

Studi literatur dilakukan untuk memahami konsep curah hujan, analisis spasial, Sistem Informasi Geografis, interpolasi IDW, serta penelitian terdahulu yang relevan.

### Step 3 — Penentuan Wilayah Penelitian

Wilayah Papua Barat dan Barat Daya ditetapkan sebagai area analisis berdasarkan cakupan wilayah administratif yang digunakan dalam penelitian.

### Step 4 — Pengumpulan Data

Data curah hujan, koordinat, dan elevasi stasiun dikumpulkan dari data pengamatan BMKG. Data batas administratif dan data referensi peta dasar digunakan sebagai data pendukung.

### Step 5 — Persiapan dan Digitasi Data

Data stasiun disiapkan dalam bentuk tabel dan dikonversi menjadi data titik berdasarkan koordinat geografis sehingga dapat digunakan dalam QGIS.

### Step 6 — Interpolasi IDW

Data titik stasiun dengan atribut curah hujan digunakan sebagai input proses interpolasi IDW.

Proses dilakukan secara terpisah untuk:

- Oktober 2020
- Oktober 2025

Hasilnya berupa raster yang menggambarkan estimasi distribusi spasial curah hujan.

### Step 7 — Clipping Hasil Interpolasi

Raster hasil interpolasi dipotong mengikuti batas wilayah penelitian sehingga analisis dan visualisasi difokuskan pada wilayah Papua Barat dan Barat Daya.

### Step 8 — Pengolahan Raster

Pengolahan raster dilakukan untuk mendukung visualisasi dan pengelompokan nilai curah hujan. Penelitian menggunakan Rasterize dan Raster Calculator sebagai bagian dari pengolahan data spasial. :contentReference[oaicite:8]{index=8}

### Step 9 — Pembuatan Kontur

Garis kontur curah hujan atau **isohyet** dibuat dari raster hasil interpolasi.

Kontur digunakan untuk menghubungkan wilayah dengan nilai curah hujan yang sama sehingga pola perubahan intensitas curah hujan antarwilayah dapat lebih mudah diamati. :contentReference[oaicite:9]{index=9}

### Step 10 — Visualisasi Peta

Hasil raster dan kontur divisualisasikan dalam bentuk peta menggunakan QGIS.

Layout peta disusun menggunakan elemen seperti:

- judul;
- legenda;
- skala;
- arah mata angin;
- sumber data;
- dan informasi wilayah penelitian.

### Step 11 — Analisis Hasil

Hasil interpolasi dianalisis untuk mengidentifikasi wilayah dengan intensitas curah hujan relatif tinggi maupun rendah serta pola distribusi spasial yang terbentuk.

Interpretasi dilakukan berdasarkan hasil interpolasi dan nilai pada lima titik pengamatan. :contentReference[oaicite:10]{index=10}

### Step 12 — Perbandingan Antarperiode

Hasil Oktober 2020 dan Oktober 2025 dibandingkan berdasarkan:

1. perubahan nilai curah hujan pada lima stasiun;
2. pola distribusi spasial;
3. rentang nilai hasil interpolasi; dan
4. pola garis kontur.

Perbandingan digunakan untuk melihat variasi distribusi antarperiode, bukan untuk menyimpulkan tren perubahan curah hujan jangka panjang.

---

## 7. Validation and Interpretation

Validasi dilakukan dengan membandingkan pola hasil interpolasi dengan informasi curah hujan dari BMKG.

Analisis mempertimbangkan bahwa nilai interpolasi pada wilayah tanpa stasiun merupakan estimasi berdasarkan hubungan spasial antar titik pengamatan.

Karena penelitian menggunakan lima stasiun dengan sebaran yang belum merata, hasil pada wilayah yang jauh dari titik pengamatan perlu ditafsirkan dengan lebih hati-hati. :contentReference[oaicite:11]{index=11}

Validasi dalam penelitian ini berfokus pada kesesuaian pola spasial dan perbandingan dengan data pengamatan yang tersedia, bukan pengujian akurasi model menggunakan jaringan stasiun validasi independen.

---

## 8. Outputs

Tahapan analisis menghasilkan beberapa jenis output:

| Output | Format | Keterangan |
|---|---|---|
| Raster interpolasi | `.tif` | Permukaan estimasi curah hujan hasil IDW |
| Raster hasil clipping | `.tif` | Hasil interpolasi yang dibatasi wilayah penelitian |
| Garis kontur | `.gpkg` | Garis isohyet hasil pengolahan raster |
| Peta penelitian | `.png` / `.jpg` | Visualisasi distribusi spasial |
| Tabel hasil | `.csv` / `.xlsx` | Rekap dan perbandingan hasil analisis |
| Proyek QGIS | `.qgz` | Proyek yang digunakan untuk pengolahan dan visualisasi |

Output penelitian digunakan untuk menganalisis distribusi curah hujan dan membandingkan kondisi Oktober 2020 dengan Oktober 2025.

---

## 9. Reproducibility Notes

Untuk mereproduksi analisis, gunakan:

- **QGIS 3.38.0-Grenoble**
- data lima stasiun pengamatan;
- data curah hujan Oktober 2020 dan Oktober 2025;
- data batas wilayah penelitian;
- parameter IDW yang tercantum pada bagian **IDW Parameters**.

---

## 10. Methodological Limitations

Beberapa keterbatasan metodologis yang perlu diperhatikan:

- Penelitian hanya menggunakan lima stasiun pengamatan.
- Sebaran titik stasiun belum merata di seluruh wilayah penelitian.
- Periode yang dibandingkan hanya Oktober 2020 dan Oktober 2025.
- IDW menghasilkan nilai estimasi pada lokasi yang tidak memiliki pengamatan langsung.
- Elevasi tidak digunakan sebagai variabel pembobot dalam interpolasi.
- Validasi tidak menggunakan jaringan stasiun independen yang terpisah dari data input.
- Hasil penelitian berfokus pada pemetaan dan perbandingan pola spasial, bukan pemodelan khusus risiko banjir, kekeringan, atau longsor.
- Perbandingan dua periode tidak dapat digunakan sebagai dasar untuk menyimpulkan tren perubahan curah hujan jangka panjang.

---

## 11. References to Research Materials

Metodologi pada dokumen ini merupakan ringkasan dari Bab III dan bagian pengolahan/analisis pada Bab IV tugas akhir.

**Firman Panggala (1212002024), Universitas Bakrie, 2026.**

Data curah hujan utama bersumber dari **Badan Meteorologi, Klimatologi, dan Geofisika (BMKG)**.

Data batas administratif dan data referensi peta digunakan sebagai data pendukung sesuai dengan sumber yang dijelaskan dalam tugas akhir.

---

