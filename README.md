# meowment-website

**1. Rescue**

a. Tampilan Daftar Laporan

- Sudah bisa menampilkan data laporan dalam bentuk card/postingan berisi foto kucing, lokasi, dan tag, status.
- Setiap kartu sudah bisa diklik untuk membuka halaman detail laporan yang berisi informasi lengkap.
- Tampilan sudah dibuat responsif untuk desktop maupun mobile.

<img width="1904" height="953" alt="image" src="https://github.com/user-attachments/assets/67417a2e-f29c-4c06-98bf-4dfb4a232420" />

b. Fitur “Kirim Laporan”

- Tombol “Kirim Laporan” di bagian atas halaman Rescue sudah berfungsi.
- Saat diklik, pengguna diarahkan ke halaman form laporan baru.
- Form berisi input yang terdiri dari nama pelapor, nomor telepon, waktu dan lokasi penemuan, tag kondisi, deskripsi, dan upload foto.
- Setelah form dikirim, muncul popup konfirmasi sukses selama 2,5 detik sebelum otomatis diarahkan kembali ke laman Rescue.

<img width="1902" height="958" alt="image" src="https://github.com/user-attachments/assets/c8a100f7-5f11-4a94-98cd-42189fef5fc8" />

c. Fitur “Laporan Anda”

- Tombol “Laporan Anda” sudah dapat digunakan.
- Saat ditekan, akan menampilkan popup di halaman yang sama berisi daftar laporan pengguna (tanpa berpindah ke halaman lain).
- Popup menampilkan data laporan dengan gaya yang rapi dan konsisten dengan desain utama.
- Pengguna dapat menutup popup tersebut untuk kembali ke tampilan utama Rescue.

<img width="1899" height="946" alt="image" src="https://github.com/user-attachments/assets/a772163a-0d01-4fab-9e3e-035bf599993f" />

d. Halaman Detail Laporan

- Sudah bisa menampilkan rincian laporan secara lengkap.
- Layout dibuat dengan judul di atas tengah, foto di sisi kiri, dan data laporan di sisi kanan.
- Terdapat tombol Kembali di kiri bawah untuk kembali ke halaman Rescue.

<img width="1920" height="951" alt="image" src="https://github.com/user-attachments/assets/9410c34f-aa06-4b83-8137-f1418ffab459" />

**2. Adopsi Kucing**

a. Tampilan Daftar Kucing Adopsi (AdoptPage.vue)

Halaman ini berfungsi sebagai direktori utama adopsi dan berhasil menampilkan data kucing dalam format card.
- Daftar Kucing : setiap kucing ditampilkan dalam card yang menyajikan informasi foto kucing, nama, umur, dan lokasi.
- Tombol Ajukan kucing untuk adopsi : di bagian header sudah berfungsi, dan ketika diklik pengguna akan diarahkan ke formulir pendaftaran kucing yang berisi data-data yang harus diisi.
- Alur Pengajuan Kucing : setelah mengisi form, ketika tombol Kirim Pengajuan ditekan maka akan muncul notifikasi Form pengajuan berhasil dikirim.
  
<img width="1906" height="948" alt="image" src="https://github.com/user-attachments/assets/52053723-4104-493c-8345-7095af8b0171" />
<img width="1905" height="949" alt="image" src="https://github.com/user-attachments/assets/1bf362b3-8f04-4963-81a1-e4317ad11c10" />

b. Halaman Detail dan Proses Adopsi (AdoptDetail.vue)

Halaman ini adalah kelanjutan dari daftar adopsi, menampilkan informasi lengkap dan memulai proses ajuan adopsi.

- Tombol Lihat detail, terdapat di setiap card kucing untuk navigasi : ketika diklik, pengguna akan diarahkan ke halaman deskripsi detail spesifik kucing tersebut.
- Galeri Foto Geser (Carousel) : di halaman detail, area foto kucing telah diimplementasikan sebagai galeri foto geser, memungkinkan pengguna melihat berbagai foto kucing (multifoto) yang tersedia.
- Tombol Ajukan Adopsi : terdapat di halaman detail; ketika diklik pengguna akan diarahkan ke formulir adopsi yang berisi data diri, alasan adopsi, dan detail pembayaran. Setelah formulir dikirim, muncul notifikasi Formulir adopsi berhasil dikirim

<img width="1900" height="944" alt="image" src="https://github.com/user-attachments/assets/e77294e0-f5a8-4f5e-a4c5-f06197f9ae41" />
<img width="1896" height="956" alt="image" src="https://github.com/user-attachments/assets/55793c2d-a9f4-4388-b477-f50f57991b5e" />

**3. Donate**

a. Form Pengisian Donasi 

- menampilkan pilihan nominal donasi
- menampilkan pilihan metode pembayaran 
- menampilkan frekuensi donasi
- Tampilan sudah dibuat responsif untuk desktop maupun mobile.

<img width="1903" height="957" alt="image" src="https://github.com/user-attachments/assets/fec908d6-5392-440e-9e28-fed9a38e4410" />

b. Fitur “Langsung Check Out”

- Tombol “Langsung Check Out” di bagian bawah halaman donate sudah berfungsi.
- Saat diklik, pengguna diarahkan ke halaman checkout sesuai dengan metode pembayaran yang dipilih.
- laman checkout donasi untuk metode transfer bank berisi ringkasan donasi, instruksi pembayaran, dan data pembayaran yang terdiri dari nomor rekening meowment, nomor rekening dan email donatur
- laman checkout donasi untuk metode Qris berisi ringkasan donasi, instruksi pembayaran, dan QR pembayaran  
- Setelah konfirmasi pembayaran, muncul popup konfirmasi sukses dan detail pembayaran
<img width="1905" height="951" alt="image" src="https://github.com/user-attachments/assets/ee09e498-3b06-4482-9c33-a143da03c59d" />
<img width="1901" height="950" alt="image" src="https://github.com/user-attachments/assets/d29a2fe7-f3e7-439c-8ad1-a066b3ffc5e9" />

**4. Cari Kucing Hilang**

a. Form Pelaporan Kucing Hilang

Pengguna dapat melaporkan kucing yang hilang dengan mengisi:

- Data kucing (nama, jenis kelamin, ras, deskripsi fisik)
- Foto kucing (multiple upload)
- Lokasi dan waktu terakhir dilihat
- Informasi kontak pelapor

Form Pencarian: Fitur untuk mencari kucing yang dilaporkan hilang oleh orang lain
<img width="1908" height="953" alt="image" src="https://github.com/user-attachments/assets/c468818a-7964-46ec-a8ad-60fcdec446cb" />

b. Sistem Pencarian Cerdas

Filter Pencarian:

- Berdasarkan lokasi (radius tertentu)
- Berdasarkan karakteristik fisik (warna, ras, jenis kelamin)
- Berdasarkan waktu kejadian
- Search Results: Menampilkan daftar kucing yang sesuai dengan kriteria pencarian

<img width="1901" height="942" alt="image" src="https://github.com/user-attachments/assets/229bdb6f-7496-444f-8ccd-b9500b4ba98d" />
<img width="1900" height="911" alt="image" src="https://github.com/user-attachments/assets/4380bad2-6a19-4c5f-9aec-feb56c30c6e7" />

c. Halaman Detail Kucing

Informasi Lengkap:

Multiple foto kucing dari berbagai angle
Deskripsi detail dan ciri-ciri khusus
Timeline perkiraan waktu hilang
Informasi kontak pelapor (tersedia tombol hubungi)

<img width="1914" height="940" alt="image" src="https://github.com/user-attachments/assets/be9ea9d9-3924-4d63-b30e-476b910f184e" />

d. My Search Page - Pantau Status

Dashboard Pribadi: Pengguna dapat memantau laporan kucing hilang mereka.

Status Timeline: Visualisasi progress pencarian dengan 4 tahapan:

 - Dilaporkan - Laporan telah diterima sistem
 - Ditemukan - Ada laporan penemuan yang match
 - Dirawat - Kucing sedang dalam perawatan
 - Diterima - Kucing telah kembali ke pemilik

Photo Gallery: Koleksi foto kucing yang dilaporkan
<img width="1900" height="948" alt="image" src="https://github.com/user-attachments/assets/9ea9faa9-a3a5-4152-8617-b19f4492f6dd" />


    
   
