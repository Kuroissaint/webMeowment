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
            <!-- Section Foto -->
            <div class="photo-section">
              <div class="photo-main">
                <img src="../assets/kucheng.png" alt="Foto Kucing Utama" class="main-photo" />
              </div>
              <div class="photo-thumbnails">
                <div class="thumbnail">
                  <img src="../assets/kucheng.png" alt="Foto Kucing 2" />
                </div>
                <div class="thumbnail">
                  <img src="../assets/kucheng.png" alt="Foto Kucing 3" />
                </div>
              </div>
            </div>

            <!-- Section Informasi -->
            <div class="detail-info">
              <div class="info-item">
                <strong>Nama</strong><span>:</span>
                <p>Milo</p>
              </div>
              <div class="info-item">
                <strong>Jenis Kelamin</strong><span>:</span>
                <p>Jantan</p>
              </div>
              <div class="info-item">
                <strong>Ras</strong><span>:</span>
                <p>Domestik Shorthair</p>
              </div>
              <div class="info-item">
                <strong>Deskripsi</strong><span>:</span>
                <p>Kucing berwarna oranye dengan corak putih di dada, sangat ramah dan aktif</p>
              </div>
              <div class="info-item">
                <strong>Terakhir kali dilihat</strong><span>:</span>
                <p>Taman Kota Bandung, 5 Nov 2025, 15:30</p>
              </div>
              <div class="info-item">
                <strong>Kontak Pelapor</strong><span>:</span>
                <p>08123456789</p>
              </div>
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
  /* --- OVERLAY & MODAL BOX --- */
    .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100;
    backdrop-filter: blur(5px);
    }

    .modal-box {
    background-color: var(--browny);
    border-radius: 20px;
    padding: 20px;
    width: 85%;
    max-width: 800px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.4);
    max-height: 85vh;
    overflow-y: auto;
    }
  
  .detail-page-content {
      max-width: 100%;
      margin: 0 auto;
  }
  
  /* --- Tombol Aksi --- */
  .action-buttons {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      gap: 15px;
  }
  
  .btn-back {
      border-radius: 8px;
      background-color: var(--darky);
      color: var(--light);
      border: none;
      padding: 8px 16px;
      cursor: pointer;
      font-size: 14px;
      font-weight: 500;
      transition: all 0.3s ease;
  }

  .btn-back:hover {
      background-color: #5a372c;
      transform: translateY(-1px);
  }
  
  .btn-contact {
      border-radius: 8px;
      background-color: var(--primary);
      color: var(--light);
      border: none;
      padding: 10px 20px;
      cursor: pointer;
      font-size: 14px;
      font-weight: 500;
      transition: all 0.3s ease;
  }

  .btn-contact:hover {
      background-color: #e07b20;
      transform: translateY(-1px);
  }
  
  /* --- Konten Detail --- */
  .detail-content-wrapper {
      display: flex;
      flex-direction: column;
      gap: 25px;
      background-color: var(--boxy);
      border-radius: 20px;
      padding: 25px;
  }
  
  /* --- Section Foto --- */
  .photo-section {
    display: flex;
    gap: 15px;
    align-items: flex-start;
  }

  .photo-main {
    flex: 2;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .main-photo {
    width: 100%;
    height: 250px;
    object-fit: cover;
    display: block;
  }

  .photo-thumbnails {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .thumbnail {
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.3s ease;
  }

  .thumbnail:hover {
    transform: scale(1.05);
  }

  .thumbnail img {
    width: 100%;
    height: 120px;
    object-fit: cover;
    display: block;
  }
  
  /* --- Section Informasi --- */
  .detail-info {
    background: white;
    border-radius: 15px;
    padding: 20px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  .info-item {
    display: grid;
    grid-template-columns: 150px 10px 1fr;
    align-items: start;
    gap: 0.5rem;
    margin-bottom: 0.8rem;
    font-size: 14px;
  }

  .info-item strong {
    color: #3c2a21;
    font-weight: 600;
  }

  .info-item span {
    font-weight: bold;
    color: #3c2a21;
  }

  .info-item p {
    margin: 0;
    color: #2c2c2c;
    line-height: 1.4;
  }

  /* Responsif untuk Tablet */
  @media (max-width: 768px) {
    .modal-box {
      width: 90%;
      padding: 15px;
      max-height: 80vh;
    }

    .action-buttons {
      flex-direction: column;
      align-items: stretch;
      gap: 10px;
    }

    .btn-back, .btn-contact {
      width: 100%;
      text-align: center;
    }

    .photo-section {
      flex-direction: column;
    }

    .main-photo {
      height: 200px;
    }

    .photo-thumbnails {
      flex-direction: row;
      justify-content: space-between;
    }

    .thumbnail img {
      height: 80px;
    }

    .info-item {
      grid-template-columns: 120px 8px 1fr;
      font-size: 13px;
    }

    .detail-content-wrapper {
      padding: 20px;
      gap: 20px;
    }
  }

  /* Responsif untuk Mobile */
  @media (max-width: 480px) {
    .modal-box {
      width: 95%;
      padding: 10px;
    }

    .detail-content-wrapper {
      padding: 15px;
      gap: 15px;
    }

    .photo-section {
      gap: 10px;
    }

    .main-photo {
      height: 180px;
    }

    .thumbnail img {
      height: 70px;
    }

    .info-item {
      grid-template-columns: 100px 5px 1fr;
      font-size: 12px;
      margin-bottom: 0.6rem;
    }

    .detail-info {
      padding: 15px;
    }
  }
  </style>
