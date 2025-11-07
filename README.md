# meowment-website

**1. Rescue**

a. Tampilan Daftar Laporan

- Sudah bisa menampilkan data laporan dalam bentuk card/postingan berisi foto kucing, lokasi, dan tag, status.
- Setiap kartu sudah bisa diklik untuk membuka halaman detail laporan yang berisi informasi lengkap.
- Tampilan sudah dibuat responsif untuk desktop maupun mobile.

b. Fitur “Kirim Laporan”

- Tombol “Kirim Laporan” di bagian atas halaman Rescue sudah berfungsi.
- Saat diklik, pengguna diarahkan ke halaman form laporan baru.
- Form berisi input yang terdiri dari nama pelapor, nomor telepon, waktu dan lokasi penemuan, tag kondisi, deskripsi, dan upload foto.
- Setelah form dikirim, muncul popup konfirmasi sukses selama 2,5 detik sebelum otomatis diarahkan kembali ke laman Rescue.

c. Fitur “Laporan Anda”

- Tombol “Laporan Anda” sudah dapat digunakan.
- Saat ditekan, akan menampilkan popup di halaman yang sama berisi daftar laporan pengguna (tanpa berpindah ke halaman lain).
- Popup menampilkan data laporan dengan gaya yang rapi dan konsisten dengan desain utama.
- Pengguna dapat menutup popup tersebut untuk kembali ke tampilan utama Rescue.

d. Halaman Detail Laporan

- Sudah bisa menampilkan rincian laporan secara lengkap.
- Layout dibuat dengan judul di atas tengah, foto di sisi kiri, dan data laporan di sisi kanan.
- Terdapat tombol Kembali di kiri bawah untuk kembali ke halaman Rescue.


**2. Adopsi Kucing**

a. Tampilan Daftar Kucing Adopsi (AdoptPage.vue)

Halaman ini berfungsi sebagai direktori utama adopsi dan berhasil menampilkan data kucing dalam format card.
- Daftar Kucing : setiap kucing ditampilkan dalam card yang menyajikan informasi foto kucing, nama, umur, dan lokasi.
- Tombol Ajukan kucing untuk adopsi : di bagian header sudah berfungsi, dan ketika diklik pengguna akan diarahkan ke formulir pendaftaran kucing yang berisi data-data yang harus diisi.
- Alur Pengajuan Kucing : setelah mengisi form, ketika tombol Kirim Pengajuan ditekan maka akan muncul notifikasi Form pengajuan berhasil dikirim.

b. Halaman Detail dan Proses Adopsi (AdoptDetail.vue)

Halaman ini adalah kelanjutan dari daftar adopsi, menampilkan informasi lengkap dan memulai proses ajuan adopsi.

- Tombol Lihat detail, terdapat di setiap card kucing untuk navigasi : ketika diklik, pengguna akan diarahkan ke halaman deskripsi detail spesifik kucing tersebut.
- Galeri Foto Geser (Carousel) : di halaman detail, area foto kucing telah diimplementasikan sebagai galeri foto geser, memungkinkan pengguna melihat berbagai foto kucing (multifoto) yang tersedia.
- Tombol Ajukan Adopsi : terdapat di halaman detail; ketika diklik pengguna akan diarahkan ke formulir adopsi yang berisi data diri, alasan adopsi, dan detail pembayaran. Setelah formulir dikirim, muncul notifikasi Formulir adopsi berhasil dikirim

**3. Donate**

a. Form Pengisian Donasi 

- menampilkan pilihan nominal donasi
- menampilkan pilihan metode pembayaran 
- menampilkan frekuensi donasi
- Tampilan sudah dibuat responsif untuk desktop maupun mobile.

b. Fitur “Langsung Check Out”

- Tombol “Langsung Check Out” di bagian bawah halaman donate sudah berfungsi.
- Saat diklik, pengguna diarahkan ke halaman checkout sesuai dengan metode pembayaran yang dipilih.
- laman checkout donasi untuk metode transfer bank berisi ringkasan donasi, instruksi pembayaran, dan data pembayaran yang terdiri dari nomor rekening meowment, nomor rekening dan email donatur
- laman checkout donasi untuk metode Qris berisi ringkasan donasi, instruksi pembayaran, dan QR pembayaran  
- Setelah konfirmasi pembayaran, muncul popup konfirmasi sukses dan detail pembayaran

**4. Cari Kucing Hilang**

a. Form Pelaporan Kucing Hilang

Pengguna dapat melaporkan kucing yang hilang dengan mengisi:

- Data kucing (nama, jenis kelamin, ras, deskripsi fisik)
- Foto kucing (multiple upload)
- Lokasi dan waktu terakhir dilihat
- Informasi kontak pelapor

Form Pencarian: Fitur untuk mencari kucing yang dilaporkan hilang oleh orang lain

b. Sistem Pencarian Cerdas

Filter Pencarian:

- Berdasarkan lokasi (radius tertentu)
- Berdasarkan karakteristik fisik (warna, ras, jenis kelamin)
- Berdasarkan waktu kejadian
- Search Results: Menampilkan daftar kucing yang sesuai dengan kriteria pencarian

c. Halaman Detail Kucing

Informasi Lengkap:

- Multiple foto kucing dari berbagai angle
- Deskripsi detail dan ciri-ciri khusus
- Timeline perkiraan waktu hilang
- Informasi kontak pelapor (tersedia tombol hubungi)
- Status Tracking: Fitur untuk melacak status pencarian kucing

d. My Search Page - Pantau Status

Dashboard Pribadi: Pengguna dapat memantau laporan kucing hilang mereka
Status Timeline: Visualisasi progress pencarian dengan 4 tahapan:
 - Dilaporkan - Laporan telah diterima sistem
 - Ditemukan - Ada laporan penemuan yang match
 - Dirawat - Kucing sedang dalam perawatan
 - Diterima - Kucing telah kembali ke pemilik

Photo Gallery: Koleksi foto kucing yang dilaporkan


    
   
