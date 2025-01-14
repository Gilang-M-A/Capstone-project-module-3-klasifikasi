*Business problem understanding*
Berikut ini adalah kumpulan data Bank yang sedang menjalankan kampanye pemasaran untuk menawarkan deposito berjangka kepada pelanggan, kampanye yang dilakukan sebagian besar dilakukan pada panggilan telepon langsung menawarkan klien bank untuk menempatkan deposito berjangka jika telah semua upaya penandaan klien telah setuju untuk menempatkan deposit - variabel target ditandai 'ya', dan jika tidak'tidak'

Target:
- Tidak(0): Tidak menempatkan deposit

- ya(1): Menempatkan deposit

*Problem statement*
Bank sedang menghadapi tantangan dalam mengoptimalkan kampanye pemasaran untuk menawarkan deposito berjangka melalui panggilan telepon langsung. Kampanye ini seringkali menghasilkan tingkat konversi yang rendah, menghabiskan sumber daya yang signifikan untuk menargetkan pelanggan yang tidak tertarik. Oleh karena itu, diperlukan solusi analitik untuk memprediksi apakah seseorang pelanggan akan menempatkan deposito ( yes) atau (tidak) berdasarkan atribut mereka

*Goals*

Maka berdasarkan permasalahan tersebut, bank ingin meningkatkan efektivitas kampanye pemasaran dengan cara memprioritaskan pelanggan yang lebih potensial untuk dihubungi, sehingga meningkatkan tingkat konversi pelanggan yang setuju membuka deposito berjangka ( deposit: yes).

*Analytic Approach:*

Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan kandidat yang mau menempatkan deposito atau tidak 

Kemudian kita akan membangun model klasifikasi yang akan membantu bank untuk dapat memprediksi probabilitas seorang kandidat yang ingin menempatkan deposito atau tidak

*Metric Evaluation*

Type 1 error: False Positive
Konsekuensi: Sia-sianya biaya kampanye, waktu dan sumber daya

Type 2 error: False negative
Konsekuensi: Kehilangan calon depositor

Berdasarkan konsekuensinya, Maka sebisa mungkin yang akan kita lakukan adalah membuat model yang dapat mengurangi cost kampanye dari bank tersebut, tetapi tanpa membuat menjadi kurangnya/tidak cukup kandidat depositor yang dibutuhkan bank, Jadi harus kita seimbangkan nanti antara precision dan recallnya dari kelas positive(kandidat depositor)

Kesimpulan:
Peningkatan Recall dan Precision:

Recall meningkat dari 62.73% menjadi 64.74%, menunjukkan bahwa model lebih baik dalam mendeteksi pelanggan yang sebenarnya positif (misalnya, pelanggan potensial yang akan merespons kampanye atau membeli produk).
Precision sedikit menurun dari 72.22% menjadi 71.24%, yang berarti model menghasilkan sedikit lebih banyak prediksi positif yang tidak relevan dibandingkan sebelumnya.
Implikasi Bisnis: Peningkatan recall dapat membantu menjangkau lebih banyak pelanggan yang berpotensi memberikan nilai bagi bisnis, meskipun dengan sedikit kompromi pada efisiensi prediksi.
Kinerja Keseluruhan Model:

Dari proses tuning hyperparameter, model dengan kombinasi optimal (100 estimators, 10 min_samples_split, dan 2 min_samples_leaf) memberikan akurasi tertinggi pada validasi silang sebesar 72.71%, dengan stabilitas yang baik (std = 1.83%).
Implikasi Bisnis: Model ini cukup stabil dan dapat diandalkan untuk memberikan hasil yang konsisten dalam situasi nyata.
Analisis Trade-off Precision-Recall:

Model menunjukkan bahwa peningkatan kemampuan mendeteksi pelanggan positif disertai sedikit penurunan keakuratan prediksi positif.
Saran Bisnis: Untuk konteks bisnis seperti kampanye pemasaran, penyesuaian lebih lanjut pada hyperparameter mungkin diperlukan untuk menyeimbangkan recall dan precision sesuai tujuan bisnis (misalnya, menjaga anggaran marketing tetap efisien sambil memperluas cakupan).
False Positives dan False Negatives:

Sebelum pembaruan: Model menghasilkan 180 False Positives (FP) dan 278 False Negatives (FN).
Setelah pembaruan: False Positives meningkat menjadi 195, tetapi False Negatives menurun menjadi 263.
Implikasi Bisnis:
Penurunan False Negatives berarti lebih banyak pelanggan target yang berhasil terdeteksi.
Peningkatan False Positives berarti model mungkin menyasar pelanggan yang tidak relevan, meningkatkan biaya pemasaran.
Evaluasi Visualisasi:

Visualisasi perbandingan metrik (precision, recall, F1-score) sebelum dan setelah tuning hyperparameter menunjukkan perbaikan signifikan dalam recall.
Rekomendasi: Visualisasi ini berguna untuk presentasi kepada tim bisnis dan pengambil keputusan, memberikan pemahaman intuitif tentang dampak model terhadap kinerja kampanye.

Contoh simulasi:
1. Hubungan Model dengan Strategi Bisnis
Targeted Marketing Campaign
Sebelum Model: Perusahaan mungkin menggunakan pendekatan mass-marketing, yaitu mengirimkan kampanye ke semua pelanggan tanpa pandang bulu. Hal ini menyebabkan biaya tinggi dan efisiensi rendah.
Setelah Model: Dengan prediksi model, perusahaan hanya menargetkan pelanggan yang memiliki probabilitas tinggi untuk merespons, berdasarkan fitur historis seperti profil pekerjaan, keseimbangan rekening, atau jenis kontak terakhir.
Contoh Simulasi: Dari data pelanggan:
Pelanggan dengan probabilitas 78% lebih diutamakan untuk kampanye karena berpotensi memberikan konversi.
Pelanggan dengan probabilitas rendah (<50%) tidak dihubungi, menghemat biaya pemasaran.
Manajemen Sumber Daya
Efisiensi Biaya: Dengan mengurangi jumlah pelanggan yang dihubungi, perusahaan dapat mengalokasikan anggaran pemasaran ke strategi lain, seperti meningkatkan penawaran untuk pelanggan berpotensi tinggi.
Contoh Perhitungan: Jika kampanye ditargetkan ke 1.000 pelanggan dengan model, dibandingkan ke semua 10.000 pelanggan:
Tanpa Model: Rp10.000 × 10.000 = Rp100 juta.
Dengan Model (20% target): Rp10.000 × 2.000 = Rp20 juta.
Hemat: Rp80 juta tanpa kehilangan target pelanggan yang potensial.
2. Meningkatkan ROI (Return on Investment)
Dengan model, perusahaan fokus pada pelanggan dengan peluang tinggi untuk menghasilkan pendapatan.

Perhitungan ROI:
Diberikan:

Biaya: Rp10.000 per pelanggan yang dihubungi.
Konversi: 20% dari pelanggan yang merespons.
Pendapatan per Konversi: Rp1.000.000.
Tanpa model:

Semua 10.000 pelanggan dihubungi.
Rata-rata respons = 10% × 10.000 = 1.000 pelanggan.
Konversi = 20% × 1.000 = 200 pelanggan.
Pendapatan: 200 × Rp1.000.000 = Rp200 juta.
Biaya: Rp100 juta.
Profit: Rp200 juta - Rp100 juta = Rp100 juta.
Dengan model:

Targetkan hanya pelanggan dengan probabilitas >50% (20% dari 10.000 = 2.000 pelanggan).
Rata-rata respons = 50% × 2.000 = 1.000 pelanggan.
Konversi = 20% × 1.000 = 200 pelanggan.
Pendapatan: 200 × Rp1.000.000 = Rp200 juta.
Biaya: Rp20 juta.
Profit: Rp200 juta - Rp20 juta = Rp180 juta.
Kesimpulan: Model meningkatkan profit sebesar Rp80 juta dengan mengurangi biaya tanpa menurunkan pendapatan.

3. Alokasi Anggaran yang Tepat
Dengan penghematan biaya dari kampanye yang lebih terfokus, perusahaan dapat:

Investasi dalam Retensi Pelanggan:
Menggunakan data pelanggan untuk menawarkan promosi khusus.
Meningkatkan Penawaran:
Meningkatkan kualitas kampanye bagi pelanggan berpotensi tinggi.
Mengembangkan Produk:
Menggunakan analisis data untuk memahami kebutuhan pelanggan yang tidak tertarget.
4. Keputusan yang Berdasarkan Data
Model ini memberikan perusahaan kemampuan untuk:

Mengukur Risiko: Mengetahui probabilitas respons membantu menghindari pelanggan yang tidak potensial.
Mengambil Keputusan Berbasis Fakta: Alih-alih bergantung pada intuisi, perusahaan menggunakan model berbasis data untuk menjalankan kampanye.
