[Peran] Kamu adalah product manager senior untuk produk Web berfitur AI.

[Tugas] Susun DRAF PRD ringkas untuk "CitraTeks Web" berdasarkan kasus berikut.

[Konteks]
Problem statement : Memasukkan teks ke komputer dari dokumen bergambar secara manual membutuhkan waktu yang lama dan rentan terhadap kesalahan pengetikan[cite: 1].
Target user        : Penulis, mahasiswa, dan staf administrasi pendataan[cite: 1].
Stakeholder lain   : Tim Developer (Frontend & Backend), Penguji Kualitas (QA), dan Pengguna Akhir.
Persona ringkas     : Budi, seorang mahasiswa tingkat akhir dan penulis lepas yang sering memfoto dokumen fisik. Ia membutuhkan alat untuk mengonversi gambar tersebut menjadi teks digital secara instan untuk laporannya agar tidak perlu mengetik ulang dari awal.
Bukti riset         : Pengujian OCR dengan modul Tesseract menggunakan bahasa Python pada 10 sampel citra (gabungan gambar internet dan foto kamera) menghasilkan tingkat akurasi konversi rata-rata 76%[cite: 1]. Tingkat akurasi spesifik mencapai rata-rata 81% untuk gambar dari internet dan 71% untuk foto dari tangkapan kamera[cite: 1].
Platform & stack    : Website — Frontend Next.js, Backend & AI Python (Tesseract).
Fitur AI inti       : Optical Character Recognition (OCR) untuk mengidentifikasi dan mengekstrak teks dari citra (RGB/Grayscale) secara otomatis[cite: 1].
Konstrain           : prototype 1 semester; data & biaya AI terbatas.

[Format output]

1. Ringkasan eksekutif;
2. Problem statement & bukti (pisahkan fakta vs asumsi);
3. Target user & stakeholder (tabel peran–kebutuhan–pengaruh);
4. Value proposition: pain yang dikurangi, gain yang diciptakan, mengapa fitur AI bukan gimmick;
5. Tujuan produk & KPI terukur (+ cara mengukurnya);
6. Scope fitur 3 bulan: tabel MoSCoW (fitur AI bertanda ★);
7. Non-goals eksplisit;
8. Asumsi & risiko utama + mitigasi.

[Aturan]

- Hanya gunakan data pada [Konteks]; bila kurang, tulis [ASUMSI-XX] lalu lanjutkan.
- Jangan menulis solusi teknis/arsitektur (itu urusan SRS/HLD/LLD).
- Bahasa Indonesia baku, format Markdown.