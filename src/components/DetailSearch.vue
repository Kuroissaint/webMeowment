<template>
    <div class="modal-overlay" @click.self="$emit('close')">
      
      <div class="modal-box">
          
        <div class="detail-page-content">
          
          <div class="action-buttons">
            <button class="btn-back" @click="$emit('close')"> 
              <span class="back">Tutup</span>
            </button>
            
            <button class="btn-contact">
              <span class="back">Hubungi Pelapor (ID: {{ catId }})</span>
            </button>
          </div>
  
          <div class="detail-content-wrapper">
            <div class="photo-section">
              <div class="photo-card large-photo">[Foto Kucing 1]</div>
            </div>
  
            <div class="detail-info">
              <div class="detail-line"><span class="label">Nama</span><span class="separator">:</span> [Nama Kucing]</div>
              <div class="detail-line"><span class="label">Jenis Kelamin</span><span class="separator">:</span> [Jenis Kelamin]</div>
              <div class="detail-line"><span class="label">Ras</span><span class="separator">:</span> [Ras]</div>
              <div class="detail-line"><span class="label">Deskripsi</span><span class="separator">:</span> [Deskripsi Kucing]</div>
              <div class="detail-line"><span class="label">Terakhir kali dilihat</span><span class="separator">:</span> [Lokasi & Waktu]</div>
            </div>
          </div>
        </div>
        
      </div>
    </div>
  </template>
  
  <script setup>
    // Menerima ID dari props, bukan dari router
    const props = defineProps({
        catId: [String, Number]
    });
    // Mendefinisikan event yang bisa dipancarkan ke parent (SearchPage.vue)
    const emit = defineEmits(['close']);
  </script>
  
  <style scoped>

  /* --- OVERLAY & MODAL BOX (CSS Kunci untuk Modal) --- */
    .modal-overlay {
    position: fixed; /* Kunci agar menutupi seluruh layar */
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0); /* Latar belakang gelap transparan */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100; /* Harus lebih tinggi dari Navbar atau elemen lain */
    backdrop-filter: blur(5px); /* Efek blur ringan pada latar belakang */
    }

    .modal-box {
    background-color: var(--browny); /* Warna latar belakang modal */
    border-radius: 30px;
    padding: 20px;
    width: 90%;
    max-width: 1200px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.4);
    max-height: 90vh; 
    overflow-y: auto; /* Memungkinkan scroll di dalam modal */
    }
  
  .detail-page-content {
      max-width: 1400px;
      margin: 0 auto;
  }
  
  /* --- Tombol Aksi (Back & Hubungi) --- */
  .action-buttons {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 30px;
  }
  
  .btn-back {
      border-radius: 8px;
      background-color: var(--darky); /* Warna gelap */
      color: var(--light);
      border: none;
      padding: 8px 16px;
      cursor: pointer;
      font-size: 16px;
      font-weight: 500;
  }
  
  .btn-contact {
      border-radius: 8px;
      background-color: var(--primary); /* Warna utama */
      color: var(--light);
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 16px;
      font-weight: 500;
  }
  
  /* --- Konten Detail --- */
  .detail-content-wrapper {
      display: flex;
      flex-direction: column;
      gap: 30px;
      background-color: var(--boxy);
      border-radius: 30px;
      padding: 30px;
  }
  
  /* --- Foto --- */
  .photo-section {
      width: 100%;
      padding: 0;
      display: flex;
      flex-direction: row;
      gap: 20px;
      justify-content: center;
  }
  
  .photo-grid {
      display: grid;
      gap: 15px; 
      width: 100%;
      max-width: 800px; /* Batasi lebar grid foto agar tidak terlalu besar */
      margin: 0 auto;

  }
  .photo-card {
      flex: 1;
      background-color: var(--light);
      border-radius: 20px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      min-height: 250px;
      aspect-ratio: 1;
  }
  
  
  /* --- Deskripsi --- */
  .detail-info {
      flex: 1; 
      padding-top: 20px;
      font-size: 18px;
      line-height: 1.8;
      width: 100%;
  }
  
  .detail-line {
      display: flex;
      margin-bottom: 10px;
  }
  
  .label {
      min-width: 150px; /* Lebar minimum untuk label (Nama, Ras, dll) */
      font-weight: 600;
  }
  
  .separator {
      margin-right: 10px;
      font-weight: 600;
  }
  </style>