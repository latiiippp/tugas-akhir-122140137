# Penerapan Curriculum Learning pada IndoBERT-lite untuk Klasifikasi Sarkasme Bahasa Indonesia

Repository ini berisi source code yang digunakan dalam penelitian tugas akhir berjudul **“Penerapan Teknik Curriculum Learning pada Pelatihan Model IndoBERT-lite untuk Klasifikasi Sarkasme dalam Teks Natural Bahasa Indonesia”**. Penelitian ini berfokus pada klasifikasi biner teks sarkasme dan nonsarkasme berbahasa Indonesia menggunakan model **IndoBERT-lite Base**.

Dataset yang digunakan berasal dari **IdSarcasm**, yaitu benchmark dataset untuk deteksi sarkasme bahasa Indonesia yang terdiri dari data **Reddit Indonesia Sarcastic** dan **Twitter Indonesia Sarcastic**. Pada penelitian ini, data Reddit digunakan sebagai data utama untuk proses pelatihan, validasi, dan pengujian model. Sementara itu, data Twitter digunakan untuk evaluasi lintas domain serta eksperimen tambahan berupa fine-tuning lanjutan.

Tahapan implementasi dalam repository ini mencakup proses prapemrosesan data, fine-tuning model IndoBERT-lite Base, pengujian beberapa konfigurasi pelatihan secara bertahap menggunakan pendekatan **one-factor-at-a-time (OFAT)**, serta penerapan **Self-Paced Dynamic Curriculum Learning (SPDCL)**. Pada metode SPDCL, tingkat kesulitan sampel dihitung menggunakan **nuclear norm** dari representasi token yang dihasilkan oleh model, kemudian urutan data pelatihan diperbarui secara dinamis berdasarkan perubahan nilai nuclear norm selama proses pelatihan.

Eksperimen dilakukan dengan beberapa skenario konfigurasi, meliputi pengujian learning rate, optimizer, scheduler, penanganan ketidakseimbangan kelas menggunakan class weighting dan focal loss, early stopping, serta variasi jumlah bin pada SPDCL. Evaluasi model dilakukan menggunakan metrik **accuracy**, **precision**, **recall**, dan **F1-score**, dengan F1-score sebagai metrik utama karena dataset memiliki distribusi kelas yang tidak seimbang.

Repository ini disediakan sebagai dokumentasi pendukung penelitian agar proses implementasi, eksperimen, dan evaluasi model dapat ditelusuri kembali secara lebih lengkap.

## Dataset

Dataset yang digunakan dalam penelitian ini berasal dari IdSarcasm. Dataset tidak disertakan secara langsung dalam repository ini. Untuk menggunakan source code, dataset dapat diperoleh melalui sumber resmi berikut:

* Link dataset: [masukkan link dataset]

## Model

Model yang digunakan dalam penelitian ini adalah:

* `indobenchmark/indobert-lite-base-p2`

Model tersebut digunakan sebagai model dasar untuk proses fine-tuning pada tugas klasifikasi sarkasme bahasa Indonesia.

## Struktur Eksperimen

Eksperimen pada penelitian ini menggunakan penamaan model sebagai berikut:

* **M0**: konfigurasi baseline
* **M1–M2**: eksperimen learning rate
* **M3–M4**: eksperimen optimizer
* **M5–M6**: eksperimen scheduler
* **M7–M9**: eksperimen penanganan ketidakseimbangan kelas
* **M10–M11**: eksperimen early stopping
* **M12–M15**: eksperimen SPDCL dengan variasi jumlah bin

## Evaluasi

Evaluasi dilakukan pada tiga skenario utama:

1. Evaluasi pada data validasi Reddit untuk memilih konfigurasi terbaik.
2. Evaluasi akhir pada data uji Reddit.
3. Evaluasi lintas domain pada data uji Twitter.

Selain itu, dilakukan juga eksperimen tambahan berupa fine-tuning lanjutan pada data Twitter untuk melihat perubahan performa model setelah disesuaikan dengan karakteristik domain Twitter.

## Catatan

Repository ini dibuat untuk keperluan dokumentasi akademik dan replikasi eksperimen penelitian. Hasil eksperimen dapat berbeda apabila terdapat perbedaan versi library, perangkat keras, seed, atau konfigurasi lingkungan eksekusi.
