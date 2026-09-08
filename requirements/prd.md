# DRAF PRD Ringkas — CitraTeks Web

## 1. Ringkasan eksekutif

CitraTeks Web adalah produk web yang membantu pengguna mengonversi teks pada dokumen bergambar menjadi teks digital secara otomatis menggunakan OCR. Produk ditujukan bagi penulis, mahasiswa, dan staf administrasi pendataan yang perlu memindahkan isi dokumen fisik tanpa mengetik ulang secara manual.

Fokus rilis awal adalah menyediakan alur sederhana: pengguna mengunggah gambar dokumen, sistem mengekstrak teks, lalu pengguna dapat meninjau dan menyalin hasilnya. Dalam batas prototype satu semester, produk memprioritaskan kegunaan inti dan transparansi atas kualitas hasil OCR.

## 2. Problem statement & bukti

### Problem statement

Memasukkan teks ke komputer dari dokumen bergambar secara manual membutuhkan waktu lama dan rentan terhadap kesalahan pengetikan. [cite: 1]

### Fakta

- Pengujian OCR pada 10 sampel citra menghasilkan akurasi konversi rata-rata 76%. [cite: 1]
- Akurasi rata-rata untuk gambar dari internet adalah 81%. [cite: 1]
- Akurasi rata-rata untuk foto dari tangkapan kamera adalah 71%. [cite: 1]
- Citra yang diproses mencakup format warna RGB dan grayscale. [cite: 1]
- Target pengguna mencakup penulis, mahasiswa, dan staf administrasi pendataan. [cite: 1]

### Asumsi

- [ASUMSI-01] Pengguna memiliki gambar dokumen yang cukup terbaca sebelum diunggah.
- [ASUMSI-02] Pengguna bersedia meninjau serta mengoreksi hasil konversi sebelum menggunakan teks untuk kebutuhan penting.
- [ASUMSI-03] Dokumen berbahasa Indonesia menjadi kebutuhan utama pada prototype awal.
- [ASUMSI-04] Pengguna lebih membutuhkan penghematan waktu input daripada hasil OCR yang sempurna tanpa koreksi.

## 3. Target user & stakeholder

| Peran | Kebutuhan utama | Pengaruh terhadap produk |
|---|---|---|
| Penulis | Mengubah kutipan, catatan, atau dokumen fisik menjadi teks yang dapat diedit | Tinggi; menentukan kemudahan alur konversi dan kualitas hasil |
| Mahasiswa | Mengonversi materi, arsip, atau dokumen pendukung laporan tanpa mengetik ulang | Tinggi; pengguna utama untuk validasi manfaat penghematan waktu |
| Staf administrasi pendataan | Memasukkan informasi dari dokumen bergambar ke proses pendataan | Tinggi; membutuhkan hasil yang mudah ditinjau dan disalin |
| Pengguna akhir | Menggunakan CitraTeks Web untuk ekstraksi teks sehari-hari | Tinggi; menjadi sumber umpan balik kegunaan produk |
| Tim Developer | Mewujudkan kebutuhan produk dalam prototype | Tinggi; menentukan kelayakan dan urutan pengerjaan |
| QA | Memastikan fungsi berjalan sesuai kebutuhan dan hasil dapat diuji | Sedang–tinggi; menjaga kualitas rilis |
| Product Manager | Menetapkan prioritas, ruang lingkup, dan ukuran keberhasilan | Tinggi; mengarahkan keputusan produk |

## 4. Value proposition

**Pain yang dikurangi**

- Waktu yang dibutuhkan untuk mengetik ulang isi dokumen bergambar.
- Risiko kesalahan ketik saat menyalin teks secara manual.
- Hambatan memanfaatkan dokumen fisik sebagai bahan laporan, tulisan, atau pendataan.

**Gain yang diciptakan**

- Teks digital tersedia lebih cepat untuk disalin dan diedit.
- Pengguna dapat memusatkan waktu pada peninjauan isi, bukan pengetikan dari nol.
- Dokumen bergambar menjadi lebih mudah digunakan kembali dalam alur kerja digital.

**Mengapa AI bukan gimmick**

OCR adalah kemampuan inti yang secara langsung melakukan pekerjaan utama pengguna: mengenali dan mengekstrak teks dari citra. Tanpa OCR, pengguna tetap harus mengetik ulang secara manual sehingga masalah utama tidak terselesaikan. Karena akurasi belum sempurna, produk harus memosisikan hasil AI sebagai draf yang dapat ditinjau pengguna, bukan sebagai kebenaran final.

## 5. Tujuan produk & KPI terukur

| Tujuan | KPI | Target awal | Cara mengukur |
|---|---|---:|---|
| Mengurangi pekerjaan pengetikan ulang | Tingkat keberhasilan konversi | [ASUMSI-05] ≥80% proses unggah menghasilkan teks | Jumlah konversi yang menghasilkan keluaran teks dibanding total percobaan |
| Menyediakan hasil yang berguna untuk pengguna | Akurasi OCR rata-rata | Mempertahankan acuan ≥76% | Bandingkan hasil OCR dengan teks referensi pada sampel uji |
| Memperbaiki kualitas pada tipe gambar yang lebih sulit | Akurasi foto kamera | [ASUMSI-06] ≥71% pada evaluasi awal | Uji terpisah menggunakan sampel foto kamera |
| Mempercepat proses digitalisasi | Penghematan waktu input | [ASUMSI-07] Proses OCR lebih cepat daripada mengetik ulang sampel yang sama | Bandingkan waktu unggah–hasil tersedia dengan waktu pengetikan manual |
| Memastikan alur mudah digunakan | Penyelesaian tugas utama | [ASUMSI-08] ≥70% pengguna uji menyelesaikan unggah hingga menyalin teks | Observasi atau pencatatan tugas dalam pengujian pengguna |

## 6. Scope fitur 3 bulan — MoSCoW

| Prioritas | Fitur | Nilai pengguna |
|---|---|---|
| Must | Unggah citra dokumen | Memulai proses konversi dari dokumen bergambar |
| Must | ★ Ekstraksi teks otomatis dari citra RGB/grayscale | Menyelesaikan pekerjaan inti: mengubah gambar menjadi teks |
| Must | Tampilan hasil teks OCR | Memungkinkan pengguna membaca hasil konversi |
| Must | Salin hasil teks | Memungkinkan pengguna menggunakan teks pada laporan, tulisan, atau pendataan |
| Must | Pesan kesalahan bila citra tidak dapat diproses | Memberi kejelasan tindakan saat proses gagal |
| Should | Penyuntingan hasil teks sebelum disalin | Memudahkan koreksi kesalahan OCR |
| Should | Indikasi bahwa hasil perlu ditinjau | Mengelola ekspektasi pengguna atas akurasi OCR |
| Should | Riwayat konversi selama sesi penggunaan | Memudahkan pengguna kembali ke hasil sebelumnya |
| Could | ★ Penanda bagian teks yang berpotensi kurang akurat | Membantu pengguna memprioritaskan pemeriksaan hasil |
| Could | Unduh hasil sebagai berkas teks | Memberi alternatif selain menyalin manual |
| Won’t (3 bulan) | Dukungan pengenalan tulisan tangan | Tidak diprioritaskan dalam prototype |
| Won’t (3 bulan) | Dukungan dokumen dengan tata letak kompleks | Risiko kualitas dan ruang lingkup terlalu besar |
| Won’t (3 bulan) | Integrasi ke layanan pihak ketiga | Tidak mendukung tujuan inti prototype |

## 7. Non-goals eksplisit

- Menjamin hasil OCR bebas kesalahan.
- Menggantikan proses verifikasi pengguna pada dokumen penting.
- Mendukung seluruh bahasa, jenis tulisan, dan kualitas gambar.
- Mengenali tulisan tangan.
- Menjadi sistem manajemen arsip dokumen.
- Menjadi alat pengolah dokumen lengkap selain ekstraksi teks dari citra.
- Membangun fitur kolaborasi, integrasi eksternal, atau otomasi pendataan lanjutan pada periode tiga bulan pertama.

## 8. Asumsi & risiko utama + mitigasi

| Asumsi / risiko | Dampak | Mitigasi |
|---|---|---|
| Akurasi rata-rata 76% belum cukup untuk semua kebutuhan pengguna | Pengguna dapat kehilangan kepercayaan pada hasil | Tampilkan hasil sebagai draf yang perlu ditinjau; sediakan penyuntingan hasil |
| Foto kamera memiliki akurasi lebih rendah (71%) dibanding gambar internet (81%) | Hasil pada foto dokumen fisik lebih sering perlu dikoreksi | Uji kualitas menggunakan sampel foto kamera dan komunikasikan kebutuhan gambar yang jelas |
| [ASUMSI-09] Kualitas gambar unggahan bervariasi | Kegagalan atau hasil teks yang tidak terbaca | Berikan pesan kesalahan yang jelas saat citra tidak dapat diproses |
| Data dan biaya AI terbatas | Ruang eksperimen serta cakupan fitur terbatas | Prioritaskan fungsi OCR inti dan evaluasi dengan sampel uji terbatas namun konsisten |
| Prototype harus selesai dalam satu semester | Risiko scope melebar dan rilis terlambat | Terapkan MoSCoW; fitur “Could” hanya dikerjakan jika fitur “Must” telah tervalidasi |
| [ASUMSI-10] Pengguna dapat mengunggah dokumen yang mengandung informasi sensitif | Risiko kekhawatiran pengguna terhadap data | Tetapkan kebutuhan penanganan data sebagai keputusan lanjutan sebelum rilis yang lebih luas |