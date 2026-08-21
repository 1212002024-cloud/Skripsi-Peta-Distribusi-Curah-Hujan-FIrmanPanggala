# Limitations

## 1. Keterbatasan Data Curah Hujan

Hasil interpolasi Inverse Distance Weighted (IDW) sangat bergantung pada kualitas, jumlah, dan distribusi spasial data curah hujan yang digunakan. Penelitian ini menggunakan lima stasiun pengamatan curah hujan, yaitu Stasiun Manokwari Selatan, Rendani, Seigun, Torea, dan Utarom. Keterbatasan jumlah titik pengamatan tersebut dapat memengaruhi kemampuan hasil interpolasi dalam merepresentasikan kondisi curah hujan pada seluruh wilayah penelitian.

Wilayah yang memiliki stasiun pengamatan atau berada lebih dekat dengan titik pengamatan memiliki dasar data observasi yang lebih kuat. Sebaliknya, wilayah yang memiliki jarak relatif jauh dari stasiun pengamatan memiliki hasil yang lebih bergantung pada estimasi berdasarkan hubungan spasial antar titik pengamatan.

## 2. Keterbatasan Metode IDW

Metode Inverse Distance Weighted (IDW) menentukan nilai pada lokasi yang tidak memiliki data pengamatan berdasarkan pengaruh nilai dari titik-titik pengamatan di sekitarnya. Titik pengamatan yang memiliki jarak lebih dekat terhadap lokasi estimasi memperoleh pengaruh yang lebih besar dibandingkan titik yang memiliki jarak lebih jauh.

Hasil interpolasi IDW dipengaruhi oleh parameter yang digunakan dalam proses interpolasi, terutama nilai *power* dan konfigurasi pengolahan raster. Pada penelitian ini digunakan nilai *power* sebesar 2. Perubahan terhadap parameter interpolasi dapat menghasilkan pola distribusi spasial yang berbeda.

Selain itu, metode IDW hanya menggunakan hubungan spasial berdasarkan jarak antar titik pengamatan dan tidak secara langsung memasukkan faktor fisik seperti elevasi, topografi, arah angin, maupun karakteristik geografis lainnya sebagai variabel pembobot. Oleh karena itu, hasil interpolasi perlu dipahami sebagai nilai estimasi berdasarkan hubungan spasial antar titik pengamatan dan bukan sebagai hasil pengukuran langsung pada seluruh wilayah penelitian.

## 3. Keterbatasan Periode Data

Penelitian ini berfokus pada data curah hujan bulan Oktober tahun 2020 dan Oktober tahun 2025. Dengan demikian, hasil penelitian belum menggambarkan variasi curah hujan pada bulan atau periode lainnya secara menyeluruh.

Penggunaan data pada periode yang terbatas menyebabkan hasil penelitian lebih tepat dipahami sebagai gambaran distribusi spasial curah hujan pada periode yang dianalisis. Hasil tersebut belum dapat digunakan untuk menggambarkan pola curah hujan jangka panjang di seluruh wilayah Papua Barat dan Barat Daya.

## 4. Keterbatasan Distribusi Spasial Stasiun

Distribusi stasiun pengamatan merupakan salah satu faktor penting dalam proses interpolasi. Lima stasiun yang digunakan dalam penelitian belum tersebar secara merata pada seluruh wilayah penelitian. Kondisi tersebut dapat menyebabkan tingkat representasi hasil interpolasi berbeda antarwilayah.

Wilayah yang berada lebih dekat dengan stasiun pengamatan memiliki dasar data observasi yang lebih kuat, sedangkan wilayah yang jauh dari titik pengamatan memiliki tingkat ketidakpastian yang lebih tinggi. Oleh karena itu, interpretasi hasil interpolasi perlu mempertimbangkan posisi dan kepadatan stasiun pengamatan yang digunakan.

## 5. Keterbatasan Wilayah Ekstrapolasi

Hasil interpolasi pada wilayah yang berada di antara titik-titik pengamatan memiliki dasar estimasi yang lebih dekat dengan data observasi. Sebaliknya, pada wilayah yang berada jauh dari stasiun pengamatan, nilai yang dihasilkan lebih bergantung pada proses estimasi spasial IDW.

Oleh karena itu, hasil penelitian tidak dimaksudkan untuk menggambarkan kondisi curah hujan secara pasti pada setiap lokasi di Papua Barat dan Barat Daya, khususnya pada wilayah yang memiliki keterbatasan data pengamatan. Nilai pada wilayah tanpa stasiun pengamatan merupakan hasil estimasi interpolasi dan bukan hasil pengukuran langsung.

## 6. Keterbatasan Penggunaan QGIS

Pengolahan data spasial dan proses interpolasi dalam penelitian ini dilakukan menggunakan Quantum GIS (QGIS). Hasil analisis bergantung pada konfigurasi proyek, sistem koordinat, parameter interpolasi, kualitas data input, serta proses pengolahan yang dilakukan.

Penelitian ini menggunakan QGIS versi 3.38.0-Grenoble, sistem koordinat EPSG:4326-WGS 84, nilai *power* sebesar 2, lima stasiun pengamatan, serta ukuran piksel raster 0.009263 pada sumbu X dan Y. Perbedaan konfigurasi tersebut dapat memengaruhi hasil raster interpolasi dan visualisasi peta yang dihasilkan.

Kesalahan dalam proses pengolahan data, seperti penggunaan sistem koordinat yang tidak sesuai, kesalahan posisi titik stasiun, atau perubahan parameter interpolasi, juga dapat memengaruhi hasil akhir penelitian.

## 7. Keterbatasan Validasi Hasil

Validasi hasil interpolasi dalam penelitian ini dilakukan secara kualitatif dengan membandingkan pola distribusi spasial hasil interpolasi IDW dengan informasi curah hujan yang terdapat pada Buletin Curah Hujan Bulanan BMKG untuk periode Oktober 2020 dan Oktober 2025.

Validasi tersebut digunakan untuk melihat kesesuaian pola spasial antara hasil interpolasi dan informasi curah hujan dari BMKG. Namun, penelitian ini belum melakukan pengukuran kesalahan secara kuantitatif menggunakan metode seperti *cross-validation*, Mean Absolute Error (MAE), atau Root Mean Square Error (RMSE).

Oleh karena itu, kesesuaian hasil interpolasi dalam penelitian ini perlu dipahami sebagai kesesuaian pola spasial dan bukan sebagai pengukuran akurasi numerik secara menyeluruh. Penelitian selanjutnya dapat melakukan validasi yang lebih komprehensif menggunakan data pengamatan yang lebih lengkap dan metode evaluasi kuantitatif.

## 8. Keterbatasan Interpretasi Hasil

Peta hasil interpolasi IDW menggambarkan pola spasial estimasi curah hujan berdasarkan data dari stasiun pengamatan yang digunakan. Perbedaan warna, nilai raster, maupun garis kontur pada peta tidak selalu menunjukkan perubahan kondisi curah hujan yang terjadi secara nyata pada setiap lokasi.

Oleh karena itu, hasil penelitian sebaiknya digunakan sebagai gambaran distribusi spasial curah hujan dan sebagai informasi pendukung untuk analisis lebih lanjut. Interpretasi hasil perlu mempertimbangkan karakteristik data, jumlah dan persebaran stasiun, parameter IDW, periode pengamatan, serta kondisi geografis wilayah penelitian.

## 9. Batasan Pengembangan Penelitian

Penelitian ini berfokus pada penerapan metode Inverse Distance Weighted (IDW) menggunakan Quantum GIS (QGIS) untuk menghasilkan interpolasi spasial curah hujan di wilayah Papua Barat dan Barat Daya. Penelitian ini tidak membandingkan secara mendalam metode IDW dengan metode interpolasi lainnya seperti Kriging, Spline, atau Natural Neighbor.

Penelitian selanjutnya dapat mengembangkan analisis dengan menggunakan data multi-temporal, menambah jumlah stasiun pengamatan, membandingkan beberapa metode interpolasi, serta menguji berbagai konfigurasi parameter IDW. Penelitian lanjutan juga dapat mempertimbangkan variabel geografis seperti elevasi dan topografi serta menggunakan metode validasi kuantitatif untuk memperoleh evaluasi akurasi yang lebih komprehensif.
