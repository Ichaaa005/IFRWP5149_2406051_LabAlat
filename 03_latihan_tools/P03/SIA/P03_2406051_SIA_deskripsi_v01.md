<!-- A. Deskripsi Use Case Ajukan KRS -->
### A. Deskripsi Use Case Ajukan KRS
| Elemen           | Deskripsi                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------|
| ID               | SIA-UC01                                                                                                         |
| Nama Use Case    | Ajukan KRS                                                                                                       |
| Aktor Utama      | Mahasiswa                                                                                                        |
| Tujuan           | Mengajukan Kartu Rencana Studi (KRS) untuk semester berjalan.                                                    |
| Prasyarat        | Mahasiswa telah login dan periode pengisian KRS sedang dibuka.                                                   |
| Alur Utama       | 1. Mahasiswa membuka menu pengajuan KRS.<br>2. Sistem menampilkan mata kuliah yang tersedia.<br>3. Mahasiswa memilih mata kuliah.<br>4. Mahasiswa mengirimkan pengajuan KRS.<br>5. Sistem menjalankan validasi KRS.<br>6. Sistem menyimpan pengajuan jika validasi berhasil.<br>7. Sistem menampilkan status pengajuan.                                                                    |
| Alur Alternatif  | Jika validasi gagal, sistem menampilkan alasan kegagalan. Mahasiswa memperbaiki pengajuan dan mengirimkannya kembali. |
| Pascakondisi     | Pengajuan berhasil tersimpan dengan status menunggu keputusan atau pengajuan belum berhasil jika validasi gagal. |

<!-- B. Deskripsi Use Case Validasi KRS -->
## B. Deskripsi Use Case Validasi KRS
| Elemen           | Deskripsi                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------|
| ID               | SIA-UC02                                                                                                         |
| Nama Use Case    | Validasi KRS                                                                                                     |
| Aktor Utama      | Tidak ada aktor eksternal langsung; dijalankan oleh sistem SIA.                                                  |
| Tujuan           | Memastikan pengajuan KRS memenuhi aturan akademik yang berlaku.                                                  |
| Prasyarat        | Mahasiswa telah mengirimkan pengajuan KRS.                                                                       |
| Alur Utama       | 1. Sistem menerima data pengajuan.<br>2. Sistem memeriksa kelengkapan data.<br>3. Sistem memeriksa kesesuaian pengajuan dengan aturan akademik.<br>4. Sistem menentukan hasil validasi.<br>5. Jika validasi berhasil, sistem mengembalikan hasil ke proses pengajuan KRS.                                                                                                                 |
| Alur Alternatif  | Jika ditemukan data tidak lengkap atau aturan tidak terpenuhi, sistem menetapkan validasi gagal dan mengirimkan informasi kesalahan ke proses pengajuan.                                                                                              |
| Pascakondisi     | Validasi berhasil sehingga pengajuan dapat dilanjutkan, atau validasi gagal sehingga pengajuan perlu diperbaiki. |

<!-- C. Deskripsi Use Case Unduh Bukti Pengajuan KRS -->
## Deskripsi Use Case Unduh Bukti Pengajuan KRS
| Elemen           | Deskripsi                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------|
| ID               | SIA-UC03                                                                                                         |
| Nama Use Case    | Unduh Bukti Pengajuan KRS                                                                                        |
| Aktor Utama      | Mahasiswa                                                                                                        |
| Tujuan           | Mendapatkan dokumen bukti pengajuan KRS.                                                                         |
| Prasyarat        | Pengajuan KRS telah tersimpan dan bukti pengajuan tersedia.                                                      |
| Alur Utama       | 1. Mahasiswa membuka halaman pengajuan KRS.<br>2. Sistem menampilkan informasi pengajuan.<br>3. Mahasiswa memilih opsi unduh bukti.<br>4. Sistem menghasilkan atau mengambil dokumen bukti pengajuan.<br>5. Sistem mengunduh dokumen ke perangkat mahasiswa.                                                                                                                            |
| Alur Alternatif  | Jika bukti belum tersedia, sistem menampilkan informasi bahwa bukti belum dapat diunduh. Mahasiswa dapat mencoba kembali setelah bukti tersedia.                                                                                                       |
| Pascakondisi     | Bukti pengajuan berhasil diunduh atau mahasiswa dapat mencoba kembali jika pengunduhan gagal.                    |

<!-- D. Deskripsi Use Case Proses Keputusan KRS -->
## D. Deskripsi Use Case Proses Keputusan KRS
| Elemen           | Deskripsi                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------|
| ID               | SIA-UC04                                                                                                         |
| Nama Use Case    | Proses Keputusan KRS                                                                                             |
| Aktor Utama      | Dosen Wali                                                                                                       |
| Tujuan           | Memproses pengajuan KRS dan menentukan persetujuan atau penolakan.                                               |
| Prasyarat        | Pengajuan KRS telah divalidasi dan tersimpan serta tersedia untuk diproses.                                      |
| Alur Utama       | 1. Dosen wali membuka daftar pengajuan KRS.<br>2. Sistem menampilkan detail pengajuan.<br>3. Dosen wali memeriksa pengajuan.<br>4. Dosen wali menentukan keputusan.<br>5. Sistem menyimpan keputusan dan memperbarui status.<br>6. Sistem menampilkan hasil keputusan kepada mahasiswa.                                                                                                     |
| Alur Alternatif — Disetujui | Dosen wali menyetujui pengajuan. Sistem mengubah status menjadi disetujui, menyimpan hasil persetujuan, dan menampilkannya kepada mahasiswa.                                                                                                  |
| Alur Alternatif — Ditolak   | Dosen wali menolak pengajuan. Sistem menyimpan status ditolak beserta alasan penolakan jika dipersyaratkan, kemudian menampilkan hasilnya kepada mahasiswa.                                                                       |
| Pascakondisi     | Status pengajuan menjadi disetujui atau ditolak sesuai keputusan dosen wali.                                     |



<!-- Uji Konsistensi -->
## Uji Konsistensi

### a. Validasi Berhasil dan Mahasiswa Tidak Mengunduh Bukti
**Hasil:** Konsisten.
**Penjelasan:** Sistem berhasil memvalidasi pengajuan KRS dan menyimpan pengajuan dengan status menunggu keputusan. Mahasiswa tidak memilih untuk mengunduh bukti pengajuan. Hal ini sesuai dengan diagram karena use case Unduh Bukti Pengajuan KRS menggunakan relasi `<<extend>>`, sehingga pengunduhan bersifat opsional. Deskripsi use case juga menunjukkan bahwa pengajuan KRS tetap berhasil meskipun bukti tidak diunduh.

### b. Validasi Gagal
**Hasil:** Konsisten.
**Penjelasan:** Sistem menemukan bahwa pengajuan KRS tidak memenuhi aturan validasi, kemudian menampilkan informasi kegagalan kepada mahasiswa. Pengajuan tidak dilanjutkan sebagai pengajuan yang berhasil dan mahasiswa dapat memperbaikinya. Hal ini sesuai dengan relasi `<<include>>` antara Ajukan KRS dan Validasi KRS karena validasi wajib dilakukan dalam proses pengajuan.

### c. Validasi Berhasil dan Mahasiswa Memilih Mengunduh Bukti
**Hasil:** Konsisten.
**Penjelasan:** Sistem berhasil memvalidasi dan menyimpan pengajuan KRS. Mahasiswa kemudian memilih untuk mengunduh bukti pengajuan. Sistem menyediakan dokumen bukti yang dapat diunduh oleh mahasiswa. Hal ini sesuai dengan diagram karena use case Unduh Bukti Pengajuan KRS merupakan perluasan opsional dari Ajukan KRS melalui relasi `<<extend>>`.

### Kesimpulan
Berdasarkan ketiga situasi tersebut, diagram dan deskripsi use case dinyatakan konsisten. Validasi KRS selalu dilakukan sebagai bagian dari proses pengajuan, sedangkan pengunduhan bukti pengajuan bersifat opsional. Jika validasi gagal, pengajuan tidak dinyatakan berhasil. Jika validasi berhasil, pengajuan dapat disimpan baik ketika mahasiswa mengunduh bukti maupun tidak.
