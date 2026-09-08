# DRAF SRS Ringkas — CitraTeks Web

## 1. Tujuan, scope, dan definisi istilah

### Tujuan

CitraTeks Web membantu pengguna mengonversi teks pada dokumen bergambar menjadi teks digital agar pekerjaan mengetik ulang dapat dikurangi. Hasil OCR diposisikan sebagai draf yang perlu ditinjau pengguna sebelum digunakan untuk kebutuhan penting.

### Scope prototype

- Unggah citra dokumen.
- Ekstraksi teks otomatis dari citra RGB atau grayscale.
- Tampilan, penyuntingan, dan penyalinan hasil teks.
- Pesan kegagalan pemrosesan.
- Riwayat konversi selama sesi penggunaan.
- Indikasi hasil yang perlu ditinjau.
- Unduh hasil sebagai berkas teks apabila kapasitas pengembangan memungkinkan.

### Di luar scope

- Pengenalan tulisan tangan.
- Dukungan tata letak dokumen kompleks.
- Jaminan hasil OCR bebas kesalahan.
- Sistem manajemen arsip dokumen.
- Integrasi dengan layanan pihak ketiga.
- Dukungan seluruh bahasa dan jenis tulisan.

### Definisi istilah

| Istilah | Definisi |
|---|---|
| Citra dokumen | Gambar yang berisi teks, berasal dari internet atau foto kamera |
| OCR | Proses otomatis untuk mengenali dan mengekstrak teks dari citra |
| Hasil OCR | Teks digital yang dihasilkan dari proses ekstraksi; bukan hasil final tanpa peninjauan |
| Foto kamera | Citra dokumen yang dihasilkan melalui tangkapan kamera |
| Gambar internet | Citra dokumen yang berasal dari sumber gambar digital/internet |
| Sesi penggunaan | Periode interaksi pengguna saat menggunakan aplikasi sebelum sesi berakhir |
| RGB | Representasi warna merah, hijau, dan biru pada citra |
| Grayscale | Representasi citra menggunakan tingkat keabuan |

## 2. User, stakeholder, lingkungan operasi, asumsi, dan dependensi

### User dan stakeholder

| Peran | Kebutuhan | Pengaruh |
|---|---|---|
| Penulis | Mengonversi kutipan atau dokumen fisik menjadi teks | Tinggi |
| Mahasiswa | Mengonversi materi dan arsip untuk laporan | Tinggi |
| Staf administrasi pendataan | Memindahkan informasi dari gambar untuk pendataan | Tinggi |
| Pengguna akhir | Menggunakan ekstraksi teks sehari-hari | Tinggi |
| Product Manager | Menetapkan prioritas dan ruang lingkup | Tinggi |
| Tim Developer | Mewujudkan kebutuhan produk | Tinggi |
| QA | Memastikan fungsi dan kualitas sesuai kebutuhan | Sedang–tinggi |

### Lingkungan operasi

| Aspek | Kebutuhan |
|---|---|
| Platform | Website |
| Pengguna | Mengakses melalui peramban web |
| Input utama | Citra dokumen RGB atau grayscale |
| Kapabilitas utama | OCR untuk menghasilkan teks digital |
| Kondisi penggunaan | Pengguna mengunggah gambar dokumen yang cukup terbaca [ASUMSI-01] |

### Asumsi dan dependensi

| ID | Asumsi / dependensi |
|---|---|
| ASUMSI-01 | Pengguna memiliki gambar dokumen yang cukup terbaca sebelum diunggah. |
| ASUMSI-02 | Pengguna bersedia meninjau dan mengoreksi hasil OCR sebelum menggunakan teks untuk kebutuhan penting. |
| ASUMSI-03 | Dokumen berbahasa Indonesia adalah kebutuhan utama prototype awal. |
| ASUMSI-04 | Pengguna lebih membutuhkan penghematan waktu input daripada hasil OCR sempurna tanpa koreksi. |
| ASUMSI-09 | Kualitas gambar unggahan dapat bervariasi dan dapat menyebabkan kegagalan pemrosesan. |
| ASUMSI-10 | Pengguna dapat mengunggah dokumen yang memuat informasi sensitif. |
| ASUMSI-11 | Batas latensi OCR prototype ditetapkan sementara untuk pengujian performa dan perlu divalidasi pada evaluasi produk. |

## 3. Functional requirements

| ID | Kebutuhan fungsional | Prioritas | Metode verifikasi |
|---|---|---|---|
| FR-01 | Sistem harus dapat menerima unggahan citra dokumen saat pengguna memulai konversi → citra tersedia untuk diproses. | Must | Uji fungsional unggah citra |
| FR-02 | Sistem harus dapat memproses citra dokumen RGB atau grayscale saat unggahan diterima → proses ekstraksi teks dimulai. | Must | Uji fungsional menggunakan sampel RGB dan grayscale |
| FR-03 | Sistem harus dapat mengekstrak teks dari citra saat pemrosesan OCR berhasil → hasil teks digital ditampilkan kepada pengguna. | Must | Uji fungsional dengan citra berisi teks dan teks referensi |
| FR-04 | Sistem harus dapat menampilkan hasil OCR saat ekstraksi selesai → pengguna dapat membaca hasil teks. | Must | Uji fungsional tampilan hasil |
| FR-05 | Sistem harus dapat menyalin hasil OCR saat pengguna meminta penyalinan → teks tersedia untuk digunakan pada aplikasi lain. | Must | Uji fungsional penyalinan teks |
| FR-06 | Sistem harus dapat menampilkan pesan kegagalan saat citra tidak dapat diproses → pengguna mengetahui bahwa hasil teks tidak tersedia. | Must | Uji negatif menggunakan citra yang gagal diproses |
| FR-07 | Sistem harus dapat memungkinkan pengguna menyunting hasil OCR saat hasil ditampilkan → perubahan teks tersedia sebelum disalin. | Should | Uji fungsional penyuntingan dan penyalinan hasil suntingan |
| FR-08 | Sistem harus dapat menampilkan indikasi bahwa hasil OCR perlu ditinjau saat hasil ditampilkan → pengguna memahami hasil merupakan draf. | Should | Inspeksi kebutuhan dan uji penerimaan pengguna |
| FR-09 | Sistem harus dapat menampilkan riwayat konversi pada sesi penggunaan saat pengguna kembali melihat hasil sebelumnya → hasil sesi dapat diakses kembali. | Should | Uji fungsional beberapa konversi dalam satu sesi |
| FR-10 | Sistem harus dapat menandai bagian teks yang berpotensi kurang akurat saat hasil OCR tersedia → pengguna dapat memprioritaskan peninjauan. | Could | Uji penerimaan berdasarkan sampel hasil OCR |
| FR-11 | Sistem harus dapat menyediakan hasil OCR sebagai berkas teks saat pengguna meminta unduhan → berkas teks dapat diperoleh pengguna. | Could | Uji fungsional unduh dan pemeriksaan isi berkas |

## 4. Non-functional requirements

| ID | Kategori ISO/IEC 25010 | Kebutuhan dan metrik | Target | Kondisi ukur | Metode verifikasi |
|---|---|---|---|---|---|
| NFR-01 | Functional suitability | Akurasi OCR rata-rata pada sampel uji | ≥76% | Evaluasi pada 10 sampel citra gabungan | Bandingkan hasil OCR dengan teks referensi |
| NFR-02 | Functional suitability | Akurasi OCR pada gambar dari internet | Acuan rata-rata ≥81% | Evaluasi pada sampel gambar internet | Bandingkan hasil OCR dengan teks referensi |
| NFR-03 | Functional suitability | Akurasi OCR pada foto kamera | ≥71% | Evaluasi pada sampel foto kamera | Bandingkan hasil OCR dengan teks referensi |
| NFR-04 | Performance efficiency | Latensi penyelesaian proses OCR | [ASUMSI-11] ≤30 detik per citra | Diukur sejak proses dimulai hingga hasil atau pesan gagal ditampilkan, pada sampel uji | Pengukuran waktu proses |
| NFR-05 | Usability | Penyelesaian alur unggah sampai salin teks oleh pengguna uji | [ASUMSI-08] ≥70% | Pengujian tugas utama tanpa bantuan langsung | Observasi dan pencatatan keberhasilan tugas |
| NFR-06 | Usability | Kejelasan status hasil OCR | Hasil ditampilkan sebagai draf yang perlu ditinjau | Saat hasil OCR ditampilkan | Uji penerimaan pengguna dan inspeksi kebutuhan |
| NFR-07 | Reliability | Keberhasilan unggahan yang menghasilkan keluaran teks | [ASUMSI-05] ≥80% | Perbandingan jumlah unggahan berhasil terhadap seluruh percobaan pada sampel uji | Pengujian fungsional dan rekap hasil |
| NFR-08 | Reliability | Kejelasan kegagalan proses | Pesan kegagalan tersedia pada seluruh skenario proses tidak berhasil | Saat citra tidak dapat diproses | Uji negatif |
| NFR-09 | Security/Privacy | Penanganan dokumen berpotensi sensitif | Kebutuhan privasi ditetapkan sebelum rilis lebih luas | Sebelum perluasan penggunaan produk | Review kebutuhan berdasarkan ASUMSI-10 |

## 5. Kebutuhan data minimum fitur AI

| Elemen | Kebutuhan |
|---|---|
| Data input | Citra dokumen yang berisi teks |
| Representasi input | RGB atau grayscale |
| Sumber citra evaluasi | Gambar internet dan foto kamera |
| Kondisi input | Citra cukup terbaca oleh pengguna sebelum diunggah [ASUMSI-01] |
| Bahasa utama | Bahasa Indonesia [ASUMSI-03] |
| Data output | Teks digital hasil OCR |
| Status output | Hasil ditampilkan sebagai draf yang dapat ditinjau dan disunting |
| Data evaluasi minimum | 10 sampel citra gabungan, sesuai bukti riset yang tersedia |
| Metrik evaluasi | Akurasi OCR rata-rata, akurasi gambar internet, dan akurasi foto kamera |

## 6. Aturan bisnis hasil riset

1. Sistem memproses citra dokumen dalam representasi RGB atau grayscale.
2. Hasil OCR tidak boleh diposisikan sebagai bebas kesalahan; pengguna perlu meninjau hasilnya sebelum digunakan.
3. Target akurasi rata-rata OCR adalah minimal 76%.
4. Target akurasi untuk foto kamera adalah minimal 71%.
5. Gambar dari internet memiliki acuan akurasi rata-rata 81%; hasil pada foto kamera berpotensi lebih rendah dan memerlukan peninjauan lebih cermat.
6. Jika citra tidak dapat diproses, sistem harus memberi pesan kegagalan kepada pengguna.
7. Pengenalan tulisan tangan dan pengolahan dokumen dengan tata letak kompleks tidak termasuk ruang lingkup prototype.
8. Kebutuhan privasi untuk dokumen sensitif harus ditetapkan sebelum penggunaan produk diperluas.

## 7. Matriks traceability

| Kebutuhan | Fitur PRD terkait | Bukti / sumber |
|---|---|---|
| FR-01 | Unggah citra | Scope Must |
| FR-02 | ★ Ekstraksi teks otomatis dari citra RGB/grayscale | Fitur AI inti dan fakta riset |
| FR-03 | ★ Ekstraksi teks otomatis | Problem statement dan value proposition |
| FR-04 | Tampilan hasil teks OCR | Scope Must |
| FR-05 | Salin hasil teks | Scope Must |
| FR-06 | Pesan kesalahan gagal proses | Scope Must; ASUMSI-09 |
| FR-07 | Penyuntingan hasil sebelum disalin | Scope Should; ASUMSI-02 |
| FR-08 | Indikasi hasil perlu ditinjau | Scope Should; hasil AI sebagai draf |
| FR-09 | Riwayat konversi sesi | Scope Should |
| FR-10 | ★ Penanda teks kurang akurat | Scope Could; risiko variasi akurasi |
| FR-11 | Unduh berkas teks | Scope Could |
| NFR-01 | Kualitas ekstraksi OCR | Bukti riset: akurasi rata-rata 76% |
| NFR-02 | Kualitas gambar internet | Bukti riset: akurasi rata-rata 81% |
| NFR-03 | Kualitas foto kamera | Bukti riset: akurasi rata-rata 71% |
| NFR-04 | Performa proses OCR | KPI percepatan digitalisasi; ASUMSI-11 |
| NFR-05 | Kemudahan alur utama | KPI penyelesaian tugas; ASUMSI-08 |
| NFR-06 | Transparansi kualitas hasil | Value proposition dan ASUMSI-02 |
| NFR-07 | Keberhasilan konversi | KPI keberhasilan unggahan; ASUMSI-05 |
| NFR-08 | Keandalan saat gagal proses | Scope Must dan ASUMSI-09 |
| NFR-09 | Privasi dokumen | Risiko utama; ASUMSI-10 |