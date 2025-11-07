<template>
  <div class="form-page">
    <div class="content-wrapper">

      <!-- LEFT SIDE: FORM -->
      <div class="form-container">

        <div class="badge">Laporan Kucing Hilang</div>

        <h1>Buat Laporan Baru 🐾</h1>
        <p>Isi data di bawah ini untuk melaporkan kucing anda yang hilang dan membutuhkan bantuan.</p>

        <form @submit.prevent="submitLaporan">

          <div class="form-group">
            <label>Nama Pelapor</label>
            <input v-model="form.nama" type="text" placeholder="Nama kamu" required />
          </div>

          <div class="form-group">
            <label>No. Telepon</label>
            <input v-model="form.telepon" type="text" placeholder="08xxxxxxxxxx" required />
          </div>

          <div class="form-group">
            <label>Waktu Hilang</label>
            <input v-model="form.waktu" type="datetime-local" required />
          </div>

          <div class="form-group">
            <label>Lokasi Terakhir Dilihat</label>
            <input v-model="form.lokasi" type="text" placeholder="Contoh: Taman Kota Bandung" required />
          </div>

          <div class="form-group">
            <label>Ras</label>
            <select v-model="form.ras" required>
              <option disabled value="">-- Pilih Ras --</option>
              <option value="Anggora">Anggora</option>
              <option value="Calico">Calico</option>
              <option value="Kampung">Kampung</option>
              <option value="Persia">Persia</option>
              <option value="Lainnya">Lainnya</option>
            </select>
          </div>

          <div class="form-group">
            <label>Tag</label>
            <select v-model="form.tag" required>
              <option disabled value="">-- Pilih Tag --</option>
              <option value="Terluka">Terluka</option>
              <option value="Tersesat">Tersesat</option>
              <option value="Anak Kucing">Anak Kucing</option>
              <option value="Butuh Makan">Butuh Makan</option>
              <option value="Lainnya">Lainnya</option>
            </select>
          </div>

          <div class="form-group">
            <label>Deskripsi</label>
            <textarea v-model="form.deskripsi" rows="4" placeholder="Tuliskan kondisi kucing"></textarea>
          </div>

          <div class="form-group">
            <label>Upload Foto</label>
            <input type="file" @change="handleFile" accept="image/*" />
          </div>

          <div class="form-buttons">
            <button type="button" class="btn-cancel" @click="router.push('/rescue')">Kembali</button>
            <button type="submit" class="btn-submit">Kirim</button>
          </div>

        </form>
      
      </div>

      <!-- RIGHT SIDE: FLOATING CAT -->
    </div>

    <!-- SUCCESS POPUP -->
    <div v-if="showPopup" class="popup-overlay">
      <div class="popup-box">
        <img src="../assets/kucingOyen.png" class="popup-cat" />
        <h2>Laporan Berhasil Dikirim 🎉🐱</h2>
        <p>Terima kasih, {{ form.nama }}! Laporanmu sedang diproses oleh tim kami.</p>
        <p class="redirect-info">Mengalihkan ke <strong>Laporan Anda</strong>...</p>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const form = ref({
  nama: '',
  telepon: '',
  waktu: '',
  lokasi: '',
  ras: '',
  tag: '',
  deskripsi: '',
  foto: null
})

const showPopup = ref(false)

const handleFile = (e) => {
  form.value.foto = e.target.files[0]
}

const submitLaporan = () => {
  showPopup.value = true

  setTimeout(() => {
    showPopup.value = false
    router.push('/rescue')
  }, 2500)
}
</script>

<style scoped>
/* PAGE BACKGROUND */
.form-page {
  background: url(../assets/paw-pattern.png);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  padding: 2rem 1rem;
  font-family: 'Poppins', sans-serif;
}

/* MAIN LAYOUT */
.content-wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 70px;
  width: 100%;
  max-width: 1200px;
}

/* FORM CARD */
.form-container {
  background: white;
  border-radius: 20px;
  padding: 2rem 1.5rem;
  width: 100%;
  max-width: 800px;
  box-shadow: 
    0 12px 28px rgba(0,0,0,0.15),
    0 4px 8px rgba(0,0,0,0.08);
  border: 1px solid rgba(255,255,255,0.4);
  backdrop-filter: blur(12px);
  position: relative;
}

/* BADGE */
.badge {
  background: #ffe3c7;
  padding: 6px 14px;
  border-radius: 20px;
  color: #7c4f3a;
  font-weight: 600;
  display: inline-block;
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

/* TEXT */
h1 {
  text-align: center;
  color: #7a4b3b;
  font-size: 1.6rem;
  margin-bottom: 0.4rem;
}

p {
  text-align: center;
  color: #5d4a42;
  margin-bottom: 2rem;
  font-size: 0.9rem;
}

/* FORM GROUP */
.form-group {
  margin-bottom: 1.3rem;
  display: flex;
  flex-direction: column;
}

label {
  font-weight: 600;
  color: #3c2a21;
  margin-bottom: 0.4rem;
  font-size: 0.95rem;
}

/* INPUT STYLES */
input, textarea, select {
  border: 1px solid #d8c5bb;
  background: #fffdfb;
  border-radius: 12px;
  padding: 0.75rem 0.9rem;
  font-size: 1rem;
  transition: all 0.25s ease;
  width: 100%;
  box-sizing: border-box;
}

input:hover, textarea:hover, select:hover {
  background: #fff8ef;
}

input:focus, textarea:focus, select:focus {
  border-color: #a07867;
  box-shadow: 0 0 0 3px rgba(188,145,123,0.35);
  outline: none;
}

/* BUTTONS */
.form-buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 2rem;
  gap: 1rem;
}

.btn-submit {
  background: linear-gradient(135deg, #a7775a, #8d5e46);
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 10px;
  cursor: pointer;
  font-weight: 600;
  transition: 0.25s ease;
  flex: 1;
}

.btn-submit:hover {
  transform: translateY(-2px);
  background: linear-gradient(135deg, #875840, #744732);
}

.btn-cancel {
  background: #e1d8d4;
  padding: 0.8rem 1.5rem;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  transition: 0.25s;
  color: #333;
  flex: 1;
}

.btn-cancel:hover {
  background: #d1c5c1;
}

/* FLOATING CAT IMAGE */
/* .cat-illustration {
  margin-top: 800px;
  
  width: 100%;
  min-width: 420px;
  object-fit: contain;
  animation: float 3s ease-in-out infinite;
  pointer-events: none;
  z-index: 2;
}*/


@keyframes float {
  0% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
  100% { transform: translateY(0); }
}

/* POPUP */
.popup-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.45);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  z-index: 1000;
}

.popup-box {
  background: white;
  padding: 1.8rem 1.5rem;
  border-radius: 18px;
  text-align: center;
  max-width: 430px;
  width: 100%;
  animation: slideUp 0.4s ease-out;
}

.popup-cat {
  width: 70px;
  margin-bottom: 1rem;
}

.popup-box h2 {
  color: #8a5e4b;
  font-size: 1.4rem;
}

.redirect-info {
  font-size: 0.85rem;
  color: #7c7c7c;
  margin-top: 1rem;
}

@keyframes slideUp {
  0% { opacity: 0; transform: translateY(15px); }
  100% { opacity: 1; transform: translateY(0); }
}

/* MEDIA QUERIES FOR RESPONSIVE DESIGN */

/* Tablet */
@media (max-width: 1024px) {
  .content-wrapper {
    gap: 40px;
  }
  
  .form-container {
    padding: 2rem 2rem;
  }
}

/* Mobile Large */
@media (max-width: 768px) {
  .form-page {
    padding: 1.5rem 0.8rem;
  }
  
  .content-wrapper {
    gap: 0;
  }
  
  .form-container {
    padding: 1.8rem 1.2rem;
    border-radius: 16px;
  }
  
  h1 {
    font-size: 1.5rem;
  }
  
  p {
    font-size: 0.85rem;
  }
  
  .form-buttons {
    flex-direction: column;
  }
  
  .btn-submit, .btn-cancel {
    width: 100%;
  }
}

/* Mobile Small */
@media (max-width: 480px) {
  .form-page {
    padding: 1rem 0.5rem;
  }
  
  .form-container {
    padding: 1.5rem 1rem;
    border-radius: 14px;
  }
  
  h1 {
    font-size: 1.3rem;
  }
  
  .badge {
    font-size: 0.8rem;
    padding: 5px 12px;
  }
  
  label {
    font-size: 0.9rem;
  }
  
  input, textarea, select {
    padding: 0.65rem 0.8rem;
    font-size: 0.95rem;
  }
  
  .popup-box {
    padding: 1.5rem 1.2rem;
  }
  
  .popup-box h2 {
    font-size: 1.2rem;
  }
}

/* Extra Small Mobile */
@media (max-width: 360px) {
  .form-container {
    padding: 1.2rem 0.8rem;
  }
  
  h1 {
    font-size: 1.2rem;
  }
  
  .form-buttons {
    margin-top: 1.5rem;
  }
}
</style>