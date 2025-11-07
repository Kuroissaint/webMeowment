<template>
    <div class="my-search-page-container">
      <div class="my-search-page-content">
  
        <div class="filter-bar">
          <div class="button-group-top">
            <router-link :to="{ name: 'Search' }" class="button inactive-link">
              <div class="laporan-anda">Laporan Lain</div>
            </router-link>
          </div>
          <button class="button-action" @click="$router.go(-1)">
            <div class="laporan-anda">Kembali</div>
          </button>
        </div>
  
        <h1 class="page-title">Pantau status kucingmu yang hilang 🐾</h1>
  
        <div class="report-detail-card">
          
          <div class="report-content-left">
            
            <div class="detail-description">
              <p class="detail-line"><strong>Nama</strong> : Molly</p>
              <p class="detail-line"><strong>Jenis Kelamin</strong> : Betina</p>
              <p class="detail-line desc-wrap">
                <strong>Deskripsi</strong> : Berwarna orange, putih, dan hitam, di bagian kepala dominan oranye
              </p>
              <p class="detail-line"><strong>Terakhir kali dilihat</strong> : [Tanggal]</p>
              <p class="detail-line"><strong>Waktu Hilang</strong> : [Waktu]</p>
              <p class="detail-line"><strong>Tag</strong> : [Tag]</p>
            </div>
            
            <div class="status-timeline">
              <div class="progress-bar"></div>
              <div class="status-steps">
                <div class="step active">Dilaporkan</div>
                <div class="step active">Ditemukan</div>
                <div class="step">Dirawat</div>
                <div class="step">Diterima</div>
              </div>
            </div>
          </div>
          
          <div class="report-photos-right">
            <div class="photo-grid">
              <div class="photo-item photo-large">
                [Foto Kucing 1]
              </div>
              <div class="photo-item photo-small-1">
                [Foto Kucing 2]
              </div>
              <div class="photo-item photo-small-2">
                [Foto Kucing 3]
              </div>
              <div class="photo-item photo-large-bottom"> 
                [Foto Kucing 4]
              </div>
            </div>
          </div>
        </div>
  
      </div>
    </div>
  </template>
  
  <script setup>
  // ...
  </script>
  
  <style scoped>
  
  .my-search-page {
    background-color: var(--browny); 
    padding: 32px 64px;
    min-height: 85vh;
    padding-bottom: 64px;
    color: var(--dark);
  }
  
  /* --- Filter Bar --- */
  .filter-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 40px;
  }
  
  .button-group-top {
    display: flex;
    gap: 16px;
    margin-left: 24px;
    padding-top: 20px;
  }
  
  .button {
    border-radius: 8px;
    padding: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
    min-width: 128px;
  }
  
  /* Style untuk link aktif (Laporan Anda) */
  .active-link {
    background-color: var(--light); /* Putih */
    border: 1px solid var(--dark);
    color: var(--dark);
  }
  
  /* Style untuk link tidak aktif (Laporan Lain) */
  .inactive-link {
    background-color: var(--dark);
    border: 1px solid var(--dark);
    color: var(--light); /* Putih */
  }
  
  .button-action {
    border-radius: 8px;
    background-color: var(--dark);
    border: 1px solid var(--dark);
    padding: 12px;
    color: var(--light);
    font-weight: 500;
    cursor: pointer;
    min-width: 137px;
  }
  
  .laporan-anda { line-height: 100%; }

  .page-title {
    font-size: 30px;
    line-height: 100%;
    margin-left: 56px;
    margin-bottom: 30px;
    font-family: 'Poppins', sans-serif;
    color: var(--dark);
  }

  /* --- Kartu Detail Laporan --- */
  .report-detail-card {
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 30px;
    background-color: var(--boxy); 
    border: 1px solid #d9d9d9;
    padding: 40px;
    display: flex; /* Gunakan Flexbox untuk tata letak Kiri-Kanan */
    gap: 40px;
    margin: 0 32px;
    min-height: 600px; /* Tambahkan tinggi minimum agar ada ruang */
  }
  
  .report-content-left {
    flex: 1; 
    max-width: 50%;
    display: flex;
    flex-direction: column;
  }
  
  /* --- 1. Deskripsi Kucing --- */
  .detail-description {
    font-size: 18px;
    line-height: 2.5; 
    color: var(--dark);
    /* PENTING: Hapus margin-bottom yang besar */
    margin-bottom: 0; 
  }
  
  /* --- 2. Status Timeline (Perbaikan Posisi Dots) --- */
  .status-timeline {
      position: relative;
      padding-top: 20px;
      margin-top: auto; 
  }
  
  .status-steps {
      display: flex;
      justify-content: space-between;
      width: 100%;
      position: relative;
      padding: 0; 
      z-index: 2;
  }
  
  /* Garis Progres */
  .progress-bar {
      position: absolute;
      top: 5px; /* Pindah ke atas */
      left: 10%;
      right: 10%;
      height: 2px;
      background-color: #767676;
      z-index: 1;
  }
  
  .step {
      position: relative;
      text-align: center;
      font-size: 16px;
      color: #767676;
      z-index: 3;
      padding-top: 15px; 
      min-width: 80px;
      background-color: var(--boxy);
  }
  
  .step::before {
      content: '';
      position: absolute;
      top: 0px; /* KUNCI: Pindah ke atas agar sejajar dengan progress-bar */
      left: 50%;
      transform: translateX(-50%);
      width: 12px; /* Besarkan sedikit dot agar terlihat */
      height: 12px;
      border-radius: 50%;
      background-color: #767676; 
      border: 3px solid var(--boxy); 
      box-sizing: content-box;
      z-index: 4;
  }
  
  .step.active { 
    color: var(--dark); 
    font-weight: 700; 
  }
  .step.active::before { 
    background-color: var(--primary); 
    box-shadow: 0 0 5px rgba(244, 139, 41, 0.7); 
  }
  
  
  /* --- Foto Kanan (4 Foto Grid) --- */
  .report-photos-right {
    flex: 1;
    max-width: 50%;
  }
  
  .photo-grid {
    display: grid;
    /* KUNCI PERBAIKAN: Tata letak 4 foto (2x2) */
    grid-template-columns: 1.5fr 1fr; /* Kolom 1 lebih lebar dari Kolom 2 */
    grid-template-rows: 1fr 1fr;
    gap: 10px;
    height: 100%; /* Memastikan grid mengisi tinggi yang tersedia */
  }
  
  .photo-item {
    background-color: #f0f0f0;
    border-radius: 10px;
    min-height: 150px;
  }
  
  /* Foto 1: Kiri Atas (Harusnya tinggi penuh di kolom kiri) */
  .photo-large {
    grid-area: 1 / 1 / 3 / 2; /* Mencakup 2 baris (tinggi penuh), kolom 1 */
  }
  
  /* Foto 2: Kanan Atas */
  .photo-small-1 {
    grid-area: 1 / 2 / 2 / 3; /* Baris 1, Kolom 2 */
  }
  
  /* Foto 3: Kanan Bawah */
  .photo-small-2 {
    grid-area: 2 / 2 / 3 / 3; /* Baris 2, Kolom 2 */
  }
  
  /* Foto 4: Kiri Bawah (Harusnya tidak ada lagi foto di sini sesuai desain) 
     -- Berdasarkan desain Anda, foto 4 berada di bawah foto 1, tapi kita akan mengatur 4 foto agar mengisi ruang 1.5fr & 1fr */
  
  /* Kita akan menggunakan tata letak grid 2x2: Kiri Besar, Kanan Kecil (2x) */
  /* Kita kembalikan ke 2x2, tapi dengan 4 slot yang diisi */
  .photo-grid {
    display: grid;
    grid-template-columns: 1fr 1fr; /* 2 kolom yang sama lebarnya */
    grid-template-rows: 1fr 1fr; /* 2 baris yang sama tingginya */
    gap: 10px;
    height: 100%;
  }
  
  .photo-large {
      grid-area: 1 / 1 / 2 / 2; /* Slot 1: Kiri Atas */
  }
  .photo-small-1 {
      grid-area: 1 / 2 / 2 / 3; /* Slot 2: Kanan Atas */
  }
  .photo-small-2 {
      grid-area: 2 / 2 / 3 / 3; /* Slot 3: Kanan Bawah */
  }
  .photo-large-bottom { 
      grid-area: 2 / 1 / 3 / 2; /* Slot 4: Kiri Bawah */
  }
  </style>