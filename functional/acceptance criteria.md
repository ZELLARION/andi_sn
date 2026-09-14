Siap. Kita bikin **DRAFT Acceptance Criteria** yang bisa langsung dipakai untuk tugas QA/test analyst. Gue buat kriterianya **terukur**, terutama untuk NFR OCR, dan US-03 ★ gue pastikan punya **happy path + edge case + timeout >30 detik**.

# DRAFT ACCEPTANCE CRITERIA — CITRATEKS WEB

## US-01 — Mengunggah Citra Dokumen

**Sebagai pengguna, saya ingin mengunggah citra dokumen agar gambar dapat diproses oleh sistem OCR.**

### Scenario 1: Berhasil mengunggah gambar RGB

```gherkin
Scenario: Berhasil mengunggah citra RGB
  Given pengguna berada pada halaman utama CitraTeks Web
  And pengguna memiliki citra dokumen dengan format RGB yang dapat dibaca sistem
  When pengguna memilih dan mengunggah citra tersebut
  Then sistem menerima citra
  And sistem menampilkan pratinjau citra
  And citra siap diproses oleh sistem OCR
```

### Scenario 2: Berhasil mengunggah gambar Grayscale

```gherkin
Scenario: Berhasil mengunggah citra Grayscale
  Given pengguna berada pada halaman utama CitraTeks Web
  And pengguna memiliki citra dokumen dengan format Grayscale
  When pengguna memilih dan mengunggah citra tersebut
  Then sistem menerima citra
  And sistem menampilkan pratinjau citra
  And citra siap diproses oleh sistem OCR
```

### Scenario 3: Gagal mengunggah citra yang tidak didukung

```gherkin
Scenario: Gagal mengunggah citra dengan format yang tidak didukung
  Given pengguna berada pada halaman unggah CitraTeks Web
  And pengguna memilih berkas yang bukan citra RGB atau Grayscale
  When pengguna mengunggah berkas tersebut
  Then sistem menolak berkas
  And sistem menampilkan pesan bahwa format citra tidak didukung
  And pengguna dapat memilih citra lain
```

**Usulan metode uji:**

* **Integration test** untuk proses upload dan validasi format.
* **UI test** untuk memastikan pratinjau muncul.
* **Uji fungsional** dengan citra RGB dan Grayscale.
* **Performance/acceptance test:** minimal **80% percobaan unggah** harus berhasil diproses.

---

# US-02 — Pemrosesan Citra RGB/Grayscale

**Sebagai pengguna, saya ingin citra RGB atau Grayscale diproses agar dapat digunakan untuk ekstraksi teks.**

### Scenario 1: Memproses citra RGB

```gherkin
Scenario: Sistem memproses citra RGB
  Given pengguna telah berhasil mengunggah citra RGB
  When pengguna memulai proses OCR
  Then sistem menerima citra RGB
  And sistem melakukan pemrosesan citra
  And citra diteruskan ke proses ekstraksi teks
```

### Scenario 2: Memproses citra Grayscale

```gherkin
Scenario: Sistem memproses citra Grayscale
  Given pengguna telah berhasil mengunggah citra Grayscale
  When pengguna memulai proses OCR
  Then sistem menerima citra Grayscale
  And sistem melakukan pemrosesan citra
  And citra diteruskan ke proses ekstraksi teks
```

### Scenario 3: Menolak jenis citra yang tidak sesuai

```gherkin
Scenario: Sistem menolak citra dengan jenis yang tidak didukung
  Given pengguna memiliki citra dengan jenis yang tidak termasuk RGB atau Grayscale
  When citra dikirim untuk diproses
  Then sistem menolak pemrosesan
  And sistem menampilkan informasi kegagalan yang jelas
```

**Usulan metode uji:**

* **Unit test** untuk fungsi validasi dan preprocessing.
* **Integration test** antara upload, preprocessing, dan OCR.
* **Functional test** menggunakan dataset RGB dan Grayscale.

---

# US-03 ★ — Ekstraksi Teks Otomatis

**Sebagai pengguna, saya ingin sistem mengekstraksi teks secara otomatis dari citra agar saya tidak perlu mengetik ulang isi dokumen.**

### Scenario 1: Happy Path — Ekstraksi berhasil

```gherkin
Scenario: Sistem berhasil mengekstraksi teks dari citra dokumen
  Given pengguna telah mengunggah citra dokumen RGB atau Grayscale yang dapat dibaca
  When pengguna memulai proses ekstraksi teks
  Then sistem menjalankan proses OCR
  And sistem menghasilkan teks dari citra
  And hasil OCR ditampilkan kepada pengguna dalam waktu <= 30 detik sejak citra diunggah
  And hasil teks diberi status "Draf/Perlu Ditinjau"
```

### Scenario 2: Edge Case — Citra dengan kontras rendah

```gherkin
Scenario: Sistem memproses citra dengan kontras rendah
  Given pengguna telah mengunggah citra dokumen RGB atau Grayscale dengan kontras rendah
  When pengguna memulai proses ekstraksi teks
  Then sistem tetap mencoba melakukan ekstraksi OCR
  And sistem menampilkan hasil ekstraksi atau pesan bahwa teks tidak dapat dikenali
  And hasil atau pesan tersebut ditampilkan dalam waktu <= 30 detik sejak citra diunggah
  And jika hasil teks tersedia, hasil diberi status "Draf/Perlu Ditinjau"
```

### Scenario 3: Edge Case — Teks sangat padat

```gherkin
Scenario: Sistem memproses citra dengan teks sangat padat
  Given pengguna telah mengunggah citra dokumen dengan kepadatan teks yang tinggi
  When pengguna memulai proses ekstraksi teks
  Then sistem menjalankan proses OCR terhadap seluruh citra
  And sistem menampilkan hasil OCR atau informasi kegagalan
  And respons ditampilkan dalam waktu <= 30 detik sejak citra diunggah
  And hasil teks yang tersedia diberi status "Draf/Perlu Ditinjau"
```

### Scenario 4: Kegagalan atau timeout lebih dari 30 detik

```gherkin
Scenario: Proses OCR melewati batas waktu 30 detik
  Given pengguna telah mengunggah citra yang valid
  And proses OCR sedang berjalan
  When proses OCR tidak menghasilkan respons sampai melewati 30 detik sejak citra diunggah
  Then sistem menghentikan atau menandai proses sebagai timeout
  And sistem menampilkan pesan kesalahan yang jelas kepada pengguna
  And sistem menyediakan opsi untuk mencoba kembali
```

**Usulan metode uji:**

* **Unit test** untuk fungsi preprocessing dan ekstraksi.
* **Integration test** untuk alur gambar → OCR → hasil teks.
* **Performance/load test** untuk memastikan respons **≤30 detik per citra**.
* **Accuracy test** menggunakan dataset pengujian.
* **Uji akurasi:** rata-rata keseluruhan **≥76%**, gambar internet **≥81%**, dan foto kamera **≥71%**.
* **Edge-case testing** untuk gambar kontras rendah dan teks padat.
* **Failure/timeout test** dengan simulasi proses OCR >30 detik.

> **Catatan QA:** nilai akurasi sebaiknya dihitung menggunakan metrik yang didefinisikan proyek, misalnya perbandingan hasil OCR dengan *ground truth*. Jangan menyatakan setiap gambar wajib memiliki akurasi ≥76%; NFR yang diberikan adalah **rata-rata**.

---

# US-04 — Melihat Hasil OCR

**Sebagai pengguna, saya ingin melihat hasil OCR agar dapat mengetahui teks yang berhasil diekstraksi.**

### Scenario 1: Menampilkan hasil OCR

```gherkin
Scenario: Pengguna dapat melihat hasil OCR
  Given proses OCR berhasil menghasilkan teks
  When sistem menyelesaikan proses ekstraksi
  Then sistem menampilkan hasil teks OCR pada halaman hasil
  And teks dapat dibaca dan dipilih oleh pengguna
  And hasil diberi status "Draf/Perlu Ditinjau"
```

### Scenario 2: Hasil OCR kosong atau tidak terbaca

```gherkin
Scenario: Sistem menampilkan informasi ketika teks tidak ditemukan
  Given pengguna telah mengunggah citra yang valid
  And proses OCR selesai tanpa menemukan teks yang dapat dikenali
  When sistem menampilkan hasil pemrosesan
  Then sistem menampilkan informasi bahwa teks tidak berhasil dikenali
  And sistem memberikan opsi untuk mengunggah citra lain
```

**Usulan metode uji:**

* **UI test**
* **Integration test**
* **Functional test** dengan citra berisi teks dan citra tanpa teks.

---

# US-05 — Menyalin Hasil OCR

**Sebagai pengguna, saya ingin menyalin hasil OCR agar dapat menggunakannya pada laporan atau dokumen lain.**

### Scenario 1: Berhasil menyalin hasil OCR

```gherkin
Scenario: Pengguna berhasil menyalin hasil OCR
  Given hasil OCR telah ditampilkan
  And hasil teks telah diperiksa oleh pengguna
  When pengguna menekan tombol "Salin Teks"
  Then sistem menyalin seluruh teks hasil OCR ke clipboard
  And sistem menampilkan konfirmasi bahwa teks berhasil disalin
```

### Scenario 2: Menyalin hasil yang telah diedit

```gherkin
Scenario: Pengguna menyalin hasil OCR yang telah diedit
  Given hasil OCR telah ditampilkan
  And pengguna telah mengubah sebagian teks
  When pengguna menekan tombol "Salin Teks"
  Then sistem menyalin teks versi terbaru
  And teks yang disalin mencerminkan hasil edit pengguna
  And sistem menampilkan konfirmasi penyalinan
```

**Usulan metode uji:**

* **UI test**
* **Functional test**
* **Integration test** antara editor dan clipboard.

---

# US-06 — Menyunting Hasil OCR

**Sebagai pengguna, saya ingin menyunting hasil OCR agar kesalahan hasil ekstraksi dapat diperbaiki.**

### Scenario 1: Mengedit teks OCR

```gherkin
Scenario: Pengguna berhasil mengedit hasil OCR
  Given hasil OCR telah ditampilkan
  When pengguna mengubah bagian teks yang dianggap salah
  Then sistem memperbarui teks sesuai perubahan pengguna
  And teks hasil edit tetap tersedia pada halaman hasil
```

### Scenario 2: Menyimpan perubahan sebelum menyalin

```gherkin
Scenario: Perubahan teks digunakan saat menyalin
  Given pengguna telah mengedit hasil OCR
  When pengguna menekan tombol "Salin Teks"
  Then sistem menyalin teks yang telah diedit
  And teks yang disalin sesuai dengan versi terakhir hasil edit
```

**Usulan metode uji:**

* **UI test**
* **Functional test**
* **Usability test** untuk memastikan pengguna dapat menemukan dan menggunakan editor.

---

# US-07 — Memahami Hasil sebagai Draf/Perlu Ditinjau

**Sebagai pengguna, saya ingin mengetahui bahwa hasil OCR perlu ditinjau agar tidak langsung menganggap hasil AI sebagai teks final.**

### Scenario 1: Indikasi draf ditampilkan

```gherkin
Scenario: Sistem menampilkan status Draf pada hasil OCR
  Given sistem berhasil menghasilkan teks OCR
  When hasil OCR ditampilkan
  Then sistem menampilkan label "Draf/Perlu Ditinjau"
  And label dapat dilihat bersamaan dengan hasil teks
```

### Scenario 2: Peringatan tetap tersedia setelah hasil diedit

```gherkin
Scenario: Status draf tetap ditampilkan setelah pengguna mengedit teks
  Given hasil OCR berstatus "Draf/Perlu Ditinjau"
  And pengguna telah mengedit sebagian hasil teks
  When pengguna melihat kembali hasil tersebut
  Then sistem tetap menampilkan status "Draf/Perlu Ditinjau"
```

### Scenario 3: Pengguna mendapat informasi untuk melakukan peninjauan

```gherkin
Scenario: Sistem memberikan informasi mengenai kebutuhan peninjauan
  Given hasil OCR telah tersedia
  When pengguna membuka hasil OCR
  Then sistem menampilkan informasi bahwa hasil perlu ditinjau
  And pengguna dapat melanjutkan ke proses penyuntingan
```

**Usulan metode uji:**

* **UI/visual test** untuk label dan pesan.
* **Usability test** untuk mengetahui apakah pengguna memahami status draf.
* **Acceptance test** untuk memastikan status selalu muncul pada hasil OCR.

---

# US-08 — Mendapatkan Informasi Kegagalan Proses

**Sebagai pengguna, saya ingin mendapatkan informasi ketika proses gagal agar mengetahui tindakan yang harus dilakukan.**

### Scenario 1: OCR gagal diproses

```gherkin
Scenario: Sistem menampilkan pesan ketika OCR gagal
  Given pengguna telah mengunggah citra yang valid
  When proses OCR mengalami kegagalan
  Then sistem menampilkan pesan kesalahan yang jelas
  And sistem tidak menampilkan hasil OCR sebagai hasil yang berhasil
  And sistem memberikan opsi untuk mencoba kembali
```

### Scenario 2: OCR mengalami timeout

```gherkin
Scenario: Sistem menangani OCR yang melewati batas 30 detik
  Given proses OCR sedang berjalan
  When proses berlangsung lebih dari 30 detik sejak citra diunggah
  Then sistem menandai proses sebagai gagal atau timeout
  And sistem menampilkan pesan kesalahan yang jelas
  And sistem memberikan opsi untuk mencoba kembali
```

### Scenario 3: Citra tidak dapat dibaca

```gherkin
Scenario: Sistem menangani citra yang tidak dapat dibaca
  Given pengguna telah mengunggah citra yang secara teknis valid
  And citra terlalu buram atau teks tidak dapat dikenali
  When sistem melakukan proses OCR
  Then sistem menampilkan informasi bahwa teks tidak dapat dikenali dengan baik
  And sistem menyarankan pengguna menggunakan citra yang lebih jelas
```

**Usulan metode uji:**

* **Integration test** dengan simulasi error OCR.
* **Negative testing** untuk citra tidak terbaca.
* **Timeout testing** dengan respons OCR >30 detik.
* **UI test** untuk pesan error.

---

# US-09 — Mengakses Riwayat Hasil Konversi dalam Satu Sesi

**Sebagai pengguna, saya ingin melihat hasil konversi sebelumnya dalam satu sesi agar dapat kembali mengakses hasil yang sudah diproses.**

### Scenario 1: Riwayat hasil tersedia

```gherkin
Scenario: Pengguna melihat riwayat hasil konversi dalam satu sesi
  Given pengguna telah berhasil melakukan beberapa proses konversi pada sesi yang sama
  When pengguna membuka menu "Riwayat"
  Then sistem menampilkan hasil konversi sebelumnya dalam sesi tersebut
  And setiap riwayat dapat dibedakan dari hasil lainnya
```

### Scenario 2: Membuka hasil dari riwayat

```gherkin
Scenario: Pengguna membuka kembali hasil konversi
  Given terdapat hasil konversi pada riwayat sesi
  When pengguna memilih salah satu riwayat
  Then sistem menampilkan kembali hasil OCR tersebut
  And hasil tetap berstatus "Draf/Perlu Ditinjau"
```

### Scenario 3: Tidak terdapat riwayat

```gherkin
Scenario: Sistem menampilkan kondisi ketika riwayat masih kosong
  Given pengguna belum melakukan konversi pada sesi saat ini
  When pengguna membuka menu "Riwayat"
  Then sistem menampilkan informasi bahwa belum terdapat riwayat konversi
  And sistem memberikan opsi untuk melakukan konversi baru
```

### Scenario 4: Riwayat tidak terbawa ke sesi baru

```gherkin
Scenario: Riwayat dibatasi pada satu sesi
  Given pengguna memiliki hasil konversi pada sesi sebelumnya
  When pengguna memulai sesi baru
  Then hasil dari sesi sebelumnya tidak ditampilkan sebagai riwayat sesi aktif
```

**Usulan metode uji:**

* **Integration test** untuk penyimpanan dan pengambilan riwayat.
* **Functional test** untuk navigasi riwayat.
* **Session test** untuk memastikan batas riwayat sesuai satu sesi.
* **UI test** untuk kondisi riwayat kosong dan berisi.

---

# Ringkasan Coverage Acceptance Criteria

| User Story  | Prioritas   |        Skenario | Fokus Pengujian                     |
| ----------- | ----------- | --------------: | ----------------------------------- |
| **US-01**   | Must Have   |               3 | Upload & validasi citra             |
| **US-02**   | Must Have   |               3 | RGB/Grayscale                       |
| **US-03 ★** | Must Have   |           **4** | AI OCR, edge case, akurasi, timeout |
| **US-04**   | Must Have   |               2 | Tampilan hasil                      |
| **US-05**   | Must Have   |               2 | Clipboard                           |
| **US-06**   | Should Have |               2 | Penyuntingan                        |
| **US-07**   | Should Have |               3 | Status Draf                         |
| **US-08**   | Must Have   |               3 | Error & fallback                    |
| **US-09**   | Should Have |               4 | Riwayat sesi                        |
| **Total**   |             | **26 skenario** |                                     |

## Target NFR yang harus ikut diverifikasi

Acceptance criteria di atas sebaiknya diuji bersama target kuantitatif berikut:

| NFR                               | Target penerimaan                      |
| --------------------------------- | -------------------------------------- |
| **Latensi OCR**                   | ≤ **30 detik/citra**                   |
| **Akurasi rata-rata keseluruhan** | ≥ **76%**                              |
| **Akurasi gambar internet**       | ≥ **81%**                              |
| **Akurasi foto kamera**           | ≥ **71%**                              |
| **Keberhasilan unggahan**         | ≥ **80%**                              |
| **Format input**                  | RGB atau Grayscale                     |
| **Timeout**                       | >30 detik → status gagal + pesan error |
| **Status hasil**                  | Selalu **Draf/Perlu Ditinjau**         |

