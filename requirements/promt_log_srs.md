[Peran] Kamu adalah requirements analyst senior.

[Tugas] Ubah PRD berikut menjadi DRAF SRS ringkas untuk produk "CitraTeks Web".

[Konteks]
  PRD hasil revisi : 
  """
  DRAF PRD Ringkas — CitraTeks Web
  1. Ringkasan eksekutif
  CitraTeks Web adalah produk web yang membantu pengguna mengonversi teks pada dokumen bergambar menjadi teks digital secara otomatis menggunakan OCR. Produk ditujukan bagi penulis, mahasiswa, dan staf administrasi pendataan yang perlu memindahkan isi dokumen fisik tanpa mengetik ulang secara manual. Fokus rilis awal adalah menyediakan alur sederhana: pengguna mengunggah gambar dokumen, sistem mengekstrak teks, lalu pengguna dapat meninjau dan menyalin hasilnya. Dalam batas prototype satu semester, produk memprioritaskan kegunaan inti dan transparansi atas kualitas hasil OCR.

  2. Problem statement & bukti
  - Problem statement: Memasukkan teks ke komputer dari dokumen bergambar secara manual membutuhkan waktu lama dan rentan terhadap kesalahan pengetikan.
  - Fakta: Pengujian OCR pada 10 sampel citra menghasilkan akurasi konversi rata-rata 76%. Akurasi rata-rata untuk gambar dari internet adalah 81%. Akurasi rata-rata untuk foto dari tangkapan kamera adalah 71%. Citra yang diproses mencakup format warna RGB dan grayscale. Target pengguna mencakup penulis, mahasiswa, dan staf administrasi pendataan.
  - Asumsi: 
    [ASUMSI-01] Pengguna memiliki gambar dokumen yang cukup terbaca sebelum diunggah.
    [ASUMSI-02] Pengguna bersedia meninjau serta mengoreksi hasil konversi sebelum menggunakan teks untuk kebutuhan penting.
    [ASUMSI-03] Dokumen berbahasa Indonesia menjadi kebutuhan utama pada prototype awal.
    [ASUMSI-04] Pengguna lebih membutuhkan penghematan waktu input daripada hasil OCR yang sempurna tanpa koreksi.

  3. Target user & stakeholder
  - Penulis: Mengubah kutipan/dokumen fisik menjadi teks (Pengaruh Tinggi).
  - Mahasiswa: Mengonversi materi/arsip tanpa mengetik ulang (Pengaruh Tinggi).
  - Staf administrasi: Memasukkan informasi dari gambar ke pendataan (Pengaruh Tinggi).
  - Pengguna akhir: Ekstraksi teks sehari-hari (Pengaruh Tinggi).
  - Tim Developer: Mewujudkan kebutuhan produk (Pengaruh Tinggi).
  - QA: Memastikan fungsi berjalan (Pengaruh Sedang-Tinggi).
  - Product Manager: Menetapkan prioritas (Pengaruh Tinggi).

  4. Value proposition
  - Pain: Waktu ketik ulang, risiko salah ketik, hambatan pemanfaatan dokumen fisik.
  - Gain: Teks digital cepat disalin/edit, hemat waktu pengetikan dari nol, dokumen gambar mudah masuk alur kerja digital.
  - Mengapa AI bukan gimmick: OCR secara langsung melakukan ekstraksi teks. Tanpa OCR, pengguna tetap harus mengetik manual. Hasil AI diposisikan sebagai draf yang dapat ditinjau.

  5. Tujuan produk & KPI terukur
  - Mengurangi pengetikan ulang -> [ASUMSI-05] ≥80% unggahan berhasil menghasilkan teks.
  - Menyediakan hasil berguna -> Akurasi OCR rata-rata ≥76%.
  - Memperbaiki kualitas gambar sulit -> Akurasi foto kamera ≥71%.
  - Mempercepat digitalisasi -> [ASUMSI-07] Proses OCR lebih cepat dari ketik manual.
  - Alur mudah digunakan -> [ASUMSI-08] ≥70% pengguna uji selesai dari unggah hingga salin teks.

  6. Scope fitur 3 bulan — MoSCoW
  - Must: Unggah citra, ★ Ekstraksi teks otomatis dari citra RGB/grayscale, Tampilan hasil teks OCR, Salin hasil teks, Pesan kesalahan gagal proses.
  - Should: Penyuntingan hasil sebelum disalin, Indikasi hasil perlu ditinjau, Riwayat konversi sesi tersebut.
  - Could: ★ Penanda teks kurang akurat, Unduh berkas teks.
  - Won’t: Pengenalan tulisan tangan, tata letak kompleks, integrasi pihak ketiga.

  7. Non-goals eksplisit
  Menjamin hasil bebas kesalahan, mengganti verifikasi manusia, mendukung semua bahasa/tulisan tangan, sistem manajemen arsip, alat pengolah dokumen lengkap.

  8. Asumsi & risiko utama + mitigasi
  - Akurasi 76% belum cukup -> Tampilkan sebagai draf yang perlu ditinjau/edit.
  - Foto kamera akurasi lebih rendah (71%) -> Komunikasikan syarat gambar jelas.
  - [ASUMSI-09] Kualitas bervariasi memicu gagal proses -> Beri pesan error jelas.
  - Data & biaya AI terbatas -> Prioritas OCR inti.
  - Prototype 1 semester -> Terapkan MoSCoW ketat.
  - [ASUMSI-10] Unggahan sensitif privasi -> Tetapkan kebijakan penanganan data sebelum rilis luas.
  """
  Acuan kualitas    : ISO/IEC 25010 (Fokus pada Functional Suitability, Performance Efficiency, Usability, Security/Privacy, Reliability)
  Prioritas         : MoSCoW
  Platform & stack  : Website — Frontend Next.js, Backend & AI Python (Tesseract OCR)

[Format output]
  1) Tujuan, scope, definisi istilah;
  2) User & stakeholder, lingkungan operasi, asumsi & dependensi;
  3) FR: tabel FR-01..FR-n — pola "Sistem harus dapat <aksi> <objek> saat <kondisi> → <output>" + ID, prioritas MoSCoW, metode verifikasi;
  4) NFR: tabel NFR-01..NFR-m — kategori ISO/IEC 25010 + metrik + target + kondisi ukur (wajib: akurasi rata-rata ≥76% & akurasi kamera ≥71%, latensi AI, keamanan/privasi [ASUMSI-10], usability);
  5) Kebutuhan data minimum fitur AI (input format RGB/Grayscale → output teks model);
  6) Aturan bisnis hasil riset;
  7) Matriks traceability: FR/NFR → fitur PRD terkait.

[Aturan]
  - Setiap FR/NFR harus dapat ditelusuri ke bukti pada PRD/riset; dilarang menambah kebutuhan tanpa bukti/asumsi yang tertulis di konteks.
  - Bila pembahasan mulai masuk rancangan arsitektur, database skema, atau desain UI, hentikan (itu urusan HLD/LLD/UIUX).
  - Gunakan Bahasa Indonesia baku dan format Markdown.