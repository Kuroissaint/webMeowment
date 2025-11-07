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
            <div class="info-item">
              <strong>Nama</strong><span>:</span>
              <p>Molly</p>
            </div>
            <div class="info-item">
              <strong>Jenis Kelamin</strong><span>:</span>
              <p>Betina</p>
            </div>
            <div class="info-item">
              <strong>Deskripsi</strong><span>:</span>
              <p>Berwarna orange, putih, dan hitam, di bagian kepala dominan oranye</p>
            </div>
            <div class="info-item">
              <strong>Terakhir kali dilihat</strong><span>:</span>
              <p>5 Nov 2025, 15:30</p>
            </div>
            <div class="info-item">
              <strong>Waktu Hilang</strong><span>:</span>
              <p>4 Nov 2025, 18:00</p>
            </div>
            <div class="info-item">
              <strong>Tag</strong><span>:</span>
              <p>Hilang, Butuh Bantuan</p>
            </div>
          </div>
          
          <div class="status-timeline">
            <div class="progress-bar">
              <div class="progress-fill" :style="{ width: progressWidth }"></div>
            </div>
            <div class="status-steps">
              <div class="step active">
                <div class="step-dot"></div>
                <span class="step-label">Dilaporkan</span>
              </div>
              <div class="step active">
                <div class="step-dot"></div>
                <span class="step-label">Ditemukan</span>
              </div>
              <div class="step">
                <div class="step-dot"></div>
                <span class="step-label">Dirawat</span>
              </div>
              <div class="step">
                <div class="step-dot"></div>
                <span class="step-label">Diterima</span>
              </div>
            </div>
          </div>
        </div>
        
        <div class="report-photos-right">
          <div class="photo-grid">
            <div class="photo-item photo-large">
              <img src="../assets/molly1.png" alt="Foto Kucing 1" />
            </div>
            <div class="photo-item photo-small-1">
              <img src="../assets/molly2.png" alt="Foto Kucing 2" />
            </div>
            <div class="photo-item photo-small-2">
              <img src="../assets/molly3.png" alt="Foto Kucing 3" />
            </div>
            <div class="photo-item photo-large-bottom"> 
              <img src="../assets/molly4.png" alt="Foto Kucing 4" />
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Progress timeline calculation
const activeSteps = ref(2) // 2 steps active (Dilaporkan, Ditemukan)
const totalSteps = 4

const progressWidth = computed(() => {
  return `${((activeSteps.value - 1) / (totalSteps - 1)) * 100}%`
})
</script>

<style scoped>
.my-search-page-container {
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
  text-decoration: none;
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
  display: flex;
  gap: 40px;
  margin: 0 32px;
  min-height: 600px;
}

.report-content-left {
  flex: 1; 
  max-width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

/* --- Deskripsi Kucing --- */
.detail-description {
  color: var(--dark);
}

.info-item {
  display: grid;
  grid-template-columns: 160px 10px 1fr;
  align-items: start;
  gap: 0.5rem;
  margin-bottom: 1rem;
  font-size: 16px;
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

/* --- Status Timeline --- */
.status-timeline {
  position: relative;
  margin-top: 40px;
  padding: 20px 0;
}

.progress-bar {
  position: absolute;
  top: 35px;
  left: 0;
  right: 0;
  height: 4px;
  background-color: #e0e0e0;
  border-radius: 2px;
  z-index: 1;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(135deg, var(--primary), #f39c12);
  border-radius: 2px;
  transition: width 0.5s ease;
}

.status-steps {
  display: flex;
  justify-content: space-between;
  position: relative;
  z-index: 2;
}

.step {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  flex: 1;
}

.step-dot {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #e0e0e0;
  border: 4px solid white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  margin-bottom: 8px;
  z-index: 3;
  transition: all 0.3s ease;
}

.step.active .step-dot {
  background-color: var(--primary);
  box-shadow: 0 0 8px rgba(244, 139, 41, 0.5);
  transform: scale(1.1);
}

.step-label {
  font-size: 14px;
  font-weight: 500;
  color: #767676;
  text-align: center;
  line-height: 1.2;
}

.step.active .step-label {
  color: var(--dark);
  font-weight: 700;
}

/* --- Foto Kanan --- */
.report-photos-right {
  flex: 1;
  max-width: 50%;
}

.photo-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 220px 220px; /* Atur tinggi baris lebih kecil */
  gap: 8px; /* Perkecil gap */
  height: auto; /* Hapus height 100% */
}

.photo-item {
  background-color: #f8f8f8;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  min-height: auto; /* Hapus min-height fixed */
}

.photo-item:hover {
  transform: translateY(-2px);
}

.photo-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.photo-large {
  grid-area: 1 / 1 / 2 / 2;
}

.photo-small-1 {
  grid-area: 1 / 2 / 2 / 3;
}

.photo-small-2 {
  grid-area: 2 / 2 / 3 / 3;
}

.photo-large-bottom {
  grid-area: 2 / 1 / 3 / 2;
}

/* Responsif untuk Tablet */
@media (max-width: 1024px) {
  .photo-grid {
    grid-template-rows: 120px 120px; /* Lebih kecil di tablet */
    gap: 6px;
  }


  .report-detail-card {
    flex-direction: column;
    gap: 30px;
    margin: 0 16px;
  }

  .report-content-left,
  .report-photos-right {
    max-width: 100%;
  }

  .photo-grid {
    height: 400px;
  }
}

/* Responsif untuk Mobile */
@media (max-width: 768px) {
  .photo-grid {
    grid-template-rows: 100px 100px; /* Lebih kecil di mobile */
    gap: 5px;
  }

  .filter-bar {
    flex-direction: column;
    gap: 15px;
    margin-bottom: 30px;
  }

  .button-group-top {
    margin-left: 0;
    padding-top: 0;
    width: 100%;
    justify-content: center;
  }

  .page-title {
    margin-left: 0;
    text-align: center;
    font-size: 24px;
    margin-bottom: 20px;
  }

  .report-detail-card {
    padding: 25px;
    margin: 0;
  }

  .info-item {
    grid-template-columns: 120px 8px 1fr;
    font-size: 14px;
    margin-bottom: 0.8rem;
  }

  .status-timeline {
    margin-top: 30px;
  }

  .step-label {
    font-size: 12px;
  }

  .photo-grid {
    height: 300px;
    gap: 10px;
  }
}

@media (max-width: 480px) {
  .photo-grid {
    grid-template-rows: 80px 80px; /* Paling kecil di mobile kecil */
    gap: 4px;
  }

  .info-item {
    grid-template-columns: 100px 5px 1fr;
    font-size: 13px;
  }

  .step-dot {
    width: 16px;
    height: 16px;
  }
}
</style>
