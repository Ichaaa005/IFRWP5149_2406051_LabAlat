<!-- Skenario tugas:  -->
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap 
pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, 
prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, 
sistem menyimpan pengajuan berstatus menunggu persetujuan dosen 
wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih 
mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS 
dan memberikan catatan keputusan.

<!-- Tabel Kebutuhan -->
| ID      | Kebutuhan tugas |
|---------|-----------------|
| SIA-R01 | Mahasiswa dapat melihat jadwal kuliah |
| SIA-R02 | Admin akademik dapat mengelola jadwal kuliah |
| SIA-R03 | Mahasiswa dapat mengajukan KRS |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS |

<!-- Batas dan Asumsi -->
• Pengguna telah terautentikasi. 
• Data mata kuliah, prasyarat, dan jadwal tersedia. 
• Validasi gagal menyebabkan pengajuan belum berhasil tersimpan. 
• Unduh bukti tidak menjadi syarat keberhasilan pengajuan. 
• KRS tersimpan belum berarti disetujui. 
• Pembayaran, pengisian nilai, dan implementasi basis data berada di luar 
tugas. 

<!-- Tabel identifikasi aktor -->
| Aktor                 | Tujuan terhadap sistem                                             |
|-----------------------|-------------------------------------------------------------       |
| Mahasiswa             | Mengajukan KRS dan mencetak bukti pengajuan                        |
| Dosen Wali            | Memproses keputusan pengajuan KRS berupa persetujuan atau penolakan|

<!-- Tabel susunan katalog usecase -->
| ID       | Nama use case                  | Peran dalam model                      |
|----------|--------------------------------|--------------------------------------  |
| SIA-UC01 | Ajukan KRS                     | Fungsi utama mahasiswa                 |
| SIA-UC02 | Validasi KRS                   | Perilaku yang disertakan pada SIA-UC01 |
| SIA-UC03 | Unduh bukti pengajuan KRS      | Tambahan bersyarat pada SIA-UC01       |
| SIA-UC04 | Proses Keputusan KRS           | Fungsi utama dosen wali                |

<!-- Relasi include -->
SIA-UC01 <<include>> SIA-UC02
Alasan: Validasi KRS menjadi bagian wajib dari proses pengajuan KRS. Pengajuan harus diperiksa terlebih dahulu berdasarkan aturan validasi yang berlaku.

<!-- Relasi exclude -->
SIA-UC03 <<extend>> SIA-UC01
Extension point: Bukti pengajuan tersedia.
Kondisi: [Mahasiswa memilih unduh bukti pengajuan KRS].
Alasan: Pengajuan KRS tetap dapat berhasil tanpa mahasiswa mengunduh bukti pengajuan.