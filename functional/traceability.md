Siap. Gue cek ulang **SRS yang ada di repo `andi_sn-main`** supaya matriksnya tidak asal dibuat. Ada satu hal penting: file `functional/use-cases.md` yang tersedia ternyata berisi **User Stories**, bukan Use Case Tahap 2. Jadi untuk kolom **ID Use Case** dan **Komponen Teknis & Model AI yang diambil dari aktor pendukung Use Case**, kita **tidak boleh mengarang**. Sesuai aturan tugas, bagian tersebut gue tandai **[BELUM LENGKAP]**.

Selain itu, **FR-10 dan FR-11 memang belum memiliki US dan Acceptance Criteria pada Tahap 4**, sehingga juga ditandai **[BELUM LENGKAP]**.

# Matriks Traceability CitraTeks Web

| ID Kebutuhan (FR)                                              | ID User Story terkait                                | ID Use Case terkait                                               | ID Acceptance Criteria terkait                                                                                                                                    | Komponen Teknis & Model AI yang terlibat                                                             | Rencana Uji                                                                                                                                                                                                  |
| -------------------------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **FR-01** — Menerima unggahan citra dokumen                    | **US-01**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-01 Scenario 1** — Berhasil RGB; **Scenario 2** — Berhasil Grayscale; **Scenario 3** — Gagal format tidak didukung                                            | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | Integration test, UI test, uji fungsional, performance/acceptance test. Target keberhasilan unggahan **≥80%**                                                                                                |
| **FR-02** — Memproses citra RGB atau grayscale                 | **US-02**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-02 Scenario 1** — Proses RGB; **Scenario 2** — Proses Grayscale; **Scenario 3** — Tolak citra tidak sesuai                                                   | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | Unit test, integration test, functional test menggunakan citra RGB dan Grayscale                                                                                                                             |
| **FR-03** — Mengekstrak teks dari citra                        | **US-03 ★**                                          | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-03 Scenario 1** — Happy Path; **Scenario 2** — Edge Case kontras rendah; **Scenario 3** — Edge Case teks padat; **Scenario 4** — Kegagalan/timeout >30 detik | **[BELUM LENGKAP]** — model AI/aktor pendukung tidak disebutkan dalam Use Case Tahap 2 yang tersedia | Unit test, integration test, performance/load test, accuracy test, edge-case testing, failure/timeout test. Akurasi rata-rata **≥76%**, internet **≥81%**, foto kamera **≥71%**, latensi **≤30 detik/citra** |
| **FR-04** — Menampilkan hasil OCR                              | **US-04**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-04 Scenario 1** — Tampil hasil; **Scenario 2** — Hasil kosong/tidak terbaca                                                                                  | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | UI test, integration test, functional test                                                                                                                                                                   |
| **FR-05** — Menyalin hasil OCR                                 | **US-05**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-05 Scenario 1** — Berhasil salin; **Scenario 2** — Salin hasil edit                                                                                          | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | UI test, functional test, integration test                                                                                                                                                                   |
| **FR-06** — Menampilkan pesan kegagalan                        | **US-08**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-08 Scenario 1** — OCR gagal; **Scenario 2** — OCR timeout >30 detik; **Scenario 3** — Citra tidak terbaca                                                    | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | Integration test, negative testing, timeout testing, UI test. Pesan kegagalan wajib tersedia pada proses yang gagal                                                                                          |
| **FR-07** — Memungkinkan pengguna menyunting hasil OCR         | **US-06**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-06 Scenario 1** — Edit teks; **Scenario 2** — Simpan perubahan sebelum salin                                                                                 | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | UI test, functional test, usability test                                                                                                                                                                     |
| **FR-08** — Menampilkan indikasi hasil OCR perlu ditinjau      | **US-07**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-07 Scenario 1** — Indikasi draf tampil; **Scenario 2** — Peringatan tetap ada setelah edit; **Scenario 3** — Informasi peninjauan                            | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | UI/visual test, usability test, acceptance test. Hasil selalu berstatus **"Draf/Perlu Ditinjau"**                                                                                                            |
| **FR-09** — Menampilkan riwayat konversi pada sesi penggunaan  | **US-09**                                            | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **US-09 Scenario 1** — Riwayat tersedia; **Scenario 2** — Buka hasil riwayat; **Scenario 3** — Riwayat kosong; **Scenario 4** — Batas satu sesi                   | **[BELUM LENGKAP]** — aktor pendukung Use Case tidak tersedia                                        | Integration test, functional test, session test, UI test                                                                                                                                                     |
| **FR-10** — Menandai bagian teks yang berpotensi kurang akurat | **[BELUM LENGKAP]** — belum memiliki US pada Tahap 1 | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **[BELUM LENGKAP]** — belum terdapat Acceptance Criteria khusus FR-10                                                                                             | **[BELUM LENGKAP]** — aktor pendukung/model AI tidak tersedia dari Use Case                          | **[BELUM LENGKAP]** — SRS hanya menetapkan verifikasi berupa uji penerimaan berdasarkan sampel hasil OCR                                                                                                     |
| **FR-11** — Menyediakan hasil OCR sebagai berkas teks          | **[BELUM LENGKAP]** — belum memiliki US pada Tahap 1 | **[BELUM LENGKAP]** — Use Case Tahap 2 tidak tersedia pada berkas | **[BELUM LENGKAP]** — belum terdapat Acceptance Criteria khusus FR-11                                                                                             | **[BELUM LENGKAP]** — aktor pendukung/model AI tidak tersedia dari Use Case                          | **[BELUM LENGKAP]** — SRS menetapkan uji fungsional unduh dan pemeriksaan isi berkas                                                                                                                         |

---

## Ringkasan Keterlacakan

| Status                                   | FR      | Keterangan                  |
| ---------------------------------------- | ------- | --------------------------- |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-01   | FR → US-01 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-02   | FR → US-02 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-03 ★ | FR → US-03 → AC + metrik AI |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-04   | FR → US-04 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-05   | FR → US-05 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-06   | FR → US-08 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-07   | FR → US-06 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-08   | FR → US-07 → AC             |
| ✅ **Lengkap sampai Acceptance Criteria** | FR-09   | FR → US-09 → AC             |
| ⚠️ **[BELUM LENGKAP]**                   | FR-10   | Belum ada US dan AC khusus  |
| ⚠️ **[BELUM LENGKAP]**                   | FR-11   | Belum ada US dan AC khusus  |

### Jalur traceability yang digunakan

Untuk requirement yang sudah lengkap:

```text
FR dari SRS
   ↓
User Story Tahap 1
   ↓
Use Case Tahap 2
   ↓
Acceptance Criteria Tahap 4
   ↓
Rencana Pengujian
```

Contoh untuk fitur AI:

```text
FR-03
  ↓
US-03 ★
  ↓
[Use Case Tahap 2 — belum tersedia]
  ↓
AC US-03:
 ├── Happy Path
 ├── Kontras Rendah
 ├── Teks Padat
 └── Timeout >30 detik
  ↓
Unit + Integration + Accuracy
+ Performance + Edge Case
+ Failure/Timeout Test
```

### Catatan yang sebaiknya dipertahankan di tugas

**Jangan mengisi `[BELUM LENGKAP]` dengan nama teknologi seperti Tesseract, Python, browser, atau server hanya berdasarkan asumsi.** SRS memang menyebut OCR sebagai kapabilitas utama, tetapi instruksi tugas secara spesifik meminta **"Komponen Teknis & Model AI yang terlibat (ambil dari aktor pendukung di Use Case)"**. Karena Use Case Tahap 2 belum ditempel/disediakan, mengisi nama aktor atau model akan menjadi **data yang dikarang**.

Begitu **hasil Use Case Tahap 2** sudah ada, matriks ini tinggal kita lengkapi pada dua kolom tersebut tanpa perlu mengubah struktur FR → US → Acceptance Criteria.

**Satu temuan penting:** SRS yang ada di repo juga menunjukkan **FR-10 (Could)** dan **FR-11 (Could)** memang berada di luar rangkaian US-01–US-09 yang diberikan pada tugas. Jadi menandainya `[BELUM LENGKAP]` adalah keputusan yang tepat dan justru menunjukkan traceability analysis-nya kritis, bukan sekadar memaksakan semua requirement terlihat lengkap.
