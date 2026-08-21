# Limitations

## 1. Keterbatasan Data Curah Hujan

Hasil interpolasi IDW sangat bergantung pada kualitas, jumlah, dan distribusi spasial data curah hujan yang digunakan. Data yang digunakan dalam penelitian ini berasal dari stasiun pengamatan yang tersedia pada wilayah penelitian. Perbedaan jumlah dan persebaran stasiun pada setiap wilayah dapat memengaruhi hasil interpolasi, terutama pada wilayah yang memiliki jumlah stasiun pengamatan lebih sedikit.

Wilayah yang memiliki stasiun pengamatan lebih banyak cenderung memiliki hasil interpolasi yang lebih terwakili oleh data pengamatan. Sebaliknya, wilayah yang memiliki jarak antarstasiun relatif jauh dapat menghasilkan nilai interpolasi yang lebih dipengaruhi oleh stasiun terdekat.

## 2. Keterbatasan Metode IDW

Metode Inverse Distance Weighted (IDW) menentukan nilai pada lokasi yang tidak memiliki data berdasarkan pengaruh nilai dari titik-titik pengamatan di sekitarnya. Pengaruh suatu titik akan semakin kecil apabila jaraknya semakin jauh dari lokasi estimasi.

Metode ini memiliki keterbatasan karena hasil interpolasi sangat dipengaruhi oleh parameter yang digunakan, terutama nilai pangkat (*power*) dan jumlah atau radius titik pengamatan yang digunakan. Perubahan parameter tersebut dapat menghasilkan pola distribusi curah hujan yang berbeda.

IDW juga tidak secara langsung mempertimbangkan faktor-faktor fisik yang dapat memengaruhi curah hujan, seperti elevasi, topografi, arah angin, dan kondisi geografis lainnya. Oleh karena itu, hasil interpolasi IDW perlu dipahami sebagai estimasi berdasarkan hubungan spasial antar titik pengamatan dan bukan sebagai representasi mutlak kondisi curah hujan di seluruh wilayah.

## 3. Keterbatasan Distribusi Spasial Stasiun

Distribusi stasiun pengamatan merupakan salah satu faktor penting dalam proses interpolasi. Apabila stasiun pengamatan terkonsentrasi pada wilayah tertentu, hasil interpolasi pada wilayah tersebut dapat memiliki tingkat representasi yang lebih baik dibandingkan wilayah yang jauh dari stasiun pengamatan.

Kondisi tersebut dapat menyebabkan adanya area yang memiliki tingkat ketidakpastian lebih tinggi, terutama pada wilayah yang berada di luar atau jauh dari jangkauan stasiun pengamatan. Oleh karena itu, interpretasi hasil peta interpolasi perlu mempertimbangkan posisi dan kepadatan stasiun curah hujan.

## 4. Keterbatasan Wilayah Ekstrapolasi

Hasil IDW pada wilayah yang berada di antara titik-titik pengamatan lebih dapat dipengaruhi oleh data observasi yang tersedia. Namun, pada area yang berada jauh dari stasiun pengamatan, hasil interpolasi dapat menjadi kurang representatif.

Oleh karena itu, hasil penelitian ini tidak dimaksudkan untuk menggambarkan kondisi curah hujan secara pasti pada setiap lokasi di Papua Barat, khususnya pada area yang memiliki keterbatasan data pengamatan.

## 5. Keterbatasan Penggunaan QGIS

Pengolahan data spasial dan proses interpolasi dalam penelitian ini dilakukan menggunakan Quantum GIS (QGIS). Hasil analisis sangat bergantung pada konfigurasi proyek, sistem koordinat, parameter interpolasi, kualitas data input, serta proses pengolahan yang dilakukan.

Kesalahan pada tahap pengolahan data, seperti sistem koordinat yang tidak sesuai, data titik yang tidak tepat, atau pengaturan parameter interpolasi yang berbeda, dapat memengaruhi hasil akhir berupa raster interpolasi dan peta curah hujan.

## 6. Keterbatasan Validasi Hasil

Hasil interpolasi merupakan nilai estimasi sehingga diperlukan validasi untuk mengetahui tingkat kesesuaiannya dengan kondisi pengamatan. Penelitian ini memiliki keterbatasan apabila jumlah data yang tersedia untuk proses validasi tidak mencukupi atau belum mencakup seluruh variasi kondisi spasial wilayah Papua Barat.

Dengan demikian, hasil interpolasi perlu digunakan dengan mempertimbangkan keterbatasan data pengamatan dan metode yang digunakan. Penelitian selanjutnya dapat melakukan validasi yang lebih komprehensif menggunakan metode seperti *cross-validation*, Mean Absolute Error (MAE), Root Mean Square Error (RMSE), atau ukuran akurasi lainnya.

## 7. Keterbatasan Interpretasi Hasil

Peta hasil interpolasi IDW menggambarkan pola spasial estimasi curah hujan berdasarkan data stasiun yang digunakan. Perbedaan warna atau nilai pada raster tidak selalu menunjukkan perubahan kondisi curah hujan yang terjadi secara nyata pada setiap lokasi.

Oleh karena itu, hasil penelitian sebaiknya digunakan sebagai gambaran distribusi spasial curah hujan dan sebagai informasi pendukung untuk analisis lebih lanjut. Interpretasi hasil perlu mempertimbangkan karakteristik data, persebaran stasiun, parameter IDW, serta kondisi geografis wilayah penelitian.

## 8. Batasan Pengembangan Penelitian

Penelitian ini berfokus pada penerapan metode IDW menggunakan QGIS untuk menghasilkan interpolasi spasial curah hujan di wilayah Papua Barat. Penelitian tidak membandingkan secara mendalam IDW dengan metode interpolasi lainnya seperti Kriging, Spline, atau Natural Neighbor.

Penelitian selanjutnya dapat mengembangkan analisis dengan membandingkan beberapa metode interpolasi, menguji beberapa nilai parameter IDW, menambahkan variabel geografis seperti elevasi, serta melakukan validasi menggunakan data pengamatan yang lebih lengkap. Pengembangan tersebut dapat digunakan untuk mengetahui metode dan parameter yang menghasilkan estimasi curah hujan dengan tingkat akurasi yang lebih baik.

