<template>
  <div class="search-page-container">
    <!-- Filter Section -->
    <div class="filter-section">
      <div class="filter-controls-group">
        <!-- Tombol kiri -->
        <div class="button-group-left">
          <router-link :to="{ name: 'MySearch' }" class="button button-filter"> 
            <div class="search-tag">Laporan Anda</div>
          </router-link>
          
        </div>

        <!-- Dropdown Search Tag -->
        <div class="search-input-center">
          <div class="select-field" @click="toggleDropdown">
            <div class="select-value">
              {{ selectedTag ? selectedTag : "Pilih Tag" }}
            </div>
            <span class="chevron-down">▼</span>
          </div>

          <div v-if="dropdownOpen" class="dropdown-list">
            <input
              v-model="searchQuery"
              type="text"
              placeholder="Cari tag..."
              class="dropdown-search"
            />
            <div
              v-for="tag in filteredTags"
              :key="tag"
              class="dropdown-item"
              @click="selectTag(tag)"
            >
              {{ tag }}
            </div>
            <div v-if="filteredTags.length === 0" class="dropdown-empty">
              Tag tidak ditemukan
            </div>
          </div>
        </div>

        <!-- Tombol kanan -->
        <router-link :to="{ name: 'Report' }" class="button-report">
          <div class="search-tag">Buat Laporan</div>
        </router-link>
      </div>

      <!-- Tag yang sudah dipilih -->
      <div class="tag-sect" v-if="selectedTags.length > 0">
        <div class="tag" v-for="(tag, index) in selectedTags" :key="index">
          <div class="search-tag">{{ tag }}</div>
          <div class="x" @click="removeTag(index)">×</div>
        </div>
      </div>
    </div>
    
    <!-- Judul -->
    <h1 class="page-title">Bantu Orang Lain Menemukan Kucingnya 🐾</h1>

    <!-- Grid Hasil -->
    <div class="results-grid">
      <div 
        v-for="cat in filteredCats" 
        :key="cat.id" 
        class="cat-card"
      >
        <div class="card-image">
          <img src="../assets/kucheng.png" alt="Foto Kucing" />
        </div>

        <div class="card-details">
          <p><strong>Status</strong> : {{ cat.status }}</p>
          <p><strong>Daerah</strong> : {{ cat.daerah }}</p>
          <p><strong>Tag</strong> : {{ cat.tags.join(', ') }}</p>
        </div>

        <button class="btn-selengkapnya" @click="openModal(cat.id)">
          Selengkapnya
        </button>
      </div>
    </div>

    <!-- Modal dengan Transisi -->
    <transition name="fade-pop">
      <DetailSearch 
        v-if="isModalOpen" 
        :cat-id="selectedCatId" 
        @close="closeModal"
      />
    </transition>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import DetailSearch from '../components/DetailSearch.vue';

// Dummy tag data
const allTags = [
  "Hitam", "Putih", "Oren", "Abu-abu", 
  "Kecil", "Dewasa", "Jantan", "Betina", 
  "Berkalung", "Tidak Berkalung", "Jinak", "Liar"
];

// Dummy data untuk kucing
const allCats = ref([
  { id: 1, status: "Hilang", daerah: "Jakarta", tags: ["Hitam", "Jantan", "Berkalung"] },
  { id: 2, status: "Ditemukan", daerah: "Bandung", tags: ["Putih", "Betina", "Jinak"] },
  { id: 3, status: "Hilang", daerah: "Surabaya", tags: ["Oren", "Jantan", "Tidak Berkalung"] },
  { id: 4, status: "Ditemukan", daerah: "Yogyakarta", tags: ["Abu-abu", "Betina", "Kecil"] },
  { id: 5, status: "Hilang", daerah: "Semarang", tags: ["Putih", "Dewasa", "Jinak"] },
  { id: 6, status: "Ditemukan", daerah: "Bali", tags: ["Oren", "Jantan", "Liar"] },
]);

// Dropdown & tag logic
const dropdownOpen = ref(false);
const searchQuery = ref("");
const selectedTag = ref(null);
const selectedTags = ref([]);

const filteredTags = computed(() => {
  return allTags.filter(tag =>
    tag.toLowerCase().includes(searchQuery.value.toLowerCase()) &&
    !selectedTags.value.includes(tag)
  );
});

function toggleDropdown() {
  dropdownOpen.value = !dropdownOpen.value;
}

function selectTag(tag) {
  if (!selectedTags.value.includes(tag)) {
    selectedTags.value.push(tag);
  }
  selectedTag.value = tag;
  dropdownOpen.value = false;
  searchQuery.value = "";
}

function removeTag(index) {
  selectedTags.value.splice(index, 1);
}

// Filter kucing berdasarkan tag
const filteredCats = computed(() => {
  if (selectedTags.value.length === 0) return allCats.value;
  return allCats.value.filter(cat =>
    selectedTags.value.every(tag => cat.tags.includes(tag))
  );
});

// Modal logic
const isModalOpen = ref(false);
const selectedCatId = ref(null);

function openModal(id) {
  selectedCatId.value = id;
  isModalOpen.value = true;
  document.body.style.overflow = 'hidden';
}

function closeModal() {
  isModalOpen.value = false;
  selectedCatId.value = null;
  document.body.style.overflow = 'auto';
}
</script>

<style scoped>
.search-page-container {
  background-color: var(--browny);
  padding: 32px 64px;
  min-height: 85vh;
  padding-bottom: 64px;
}

/* --- Filter Section --- */
.filter-controls-group {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 20px;
}

.button-group-left {
  display: flex;
  align-items: center;
  gap: 16px;
}

.button-filter, .button-report {
  border-radius: 8px;
  background-color: var(--dark);
  border: 1px solid var(--dark);
  padding: 12px 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  color: white;
  cursor: pointer;
  min-width: 128px;
  white-space: nowrap;
  transition: 0.2s;
}

.button-filter:hover, .button-report:hover {
  background-color: #40352d;
}

.search-input-center {
  flex: 1;
  display: flex;
  justify-content: center;
  position: relative;
}

.select-field {
  background-color: white;
  border: 1px solid #d9d9d9;
  border-radius: 8px;
  padding: 12px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  min-width: 200px;
  max-width: 300px;
  width: 100%;
  color: var(--dark);
  cursor: pointer;
}

.chevron-down {
  font-size: 12px;
}

/* Dropdown tag list */
.dropdown-list {
  position: absolute;
  top: 105%;
  width: 100%;
  background-color: white;
  border-radius: 8px;
  border: 1px solid #ddd;
  box-shadow: 0px 4px 10px rgba(0,0,0,0.1);
  max-height: 200px;
  overflow-y: auto;
  z-index: 5;
}

.dropdown-search {
  width: 100%;
  border: none;
  border-bottom: 1px solid #eee;
  padding: 10px 12px;
  font-size: 14px;
  outline: none;
}

.dropdown-item {
  padding: 10px 12px;
  cursor: pointer;
  transition: background 0.2s;
}

.dropdown-item:hover {
  background-color: #f8f8f8;
}

.dropdown-empty {
  padding: 12px;
  font-size: 14px;
  color: #aaa;
  text-align: center;
}

/* --- Tag Section --- */
.tag-sect {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 40px;
}

.tag {
  border-radius: 8px;
  background-color: var(--dark);
  padding: 8px 12px;
  display: flex;
  align-items: center;
  gap: 8px;
  color: white;
  font-size: 16px;
  cursor: default;
}

.x {
  cursor: pointer;
  font-weight: 700;
}

/* --- Page Title --- */
.page-title {
  font-size: 30px;
  line-height: 100%;
  font-family: 'Poppins', sans-serif;
  color: var(--dark);
  margin-left: 33px;
  margin-bottom: 30px;
}

/* --- CARD BARU - GABUNGAN RESCUE + SEARCH --- */
.results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  padding: 0 33px;
}

.cat-card {
  background-color: white;
  border-radius: 20px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  overflow: hidden;
  transition: transform 0.25s, box-shadow 0.25s;
  display: flex;
  flex-direction: column;
  padding: 20px;
}

.cat-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}

/* GAMBAR SEPERTI RESCUE */
.card-image {
  width: 100%;
  height: 200px;
  overflow: hidden;
  border-radius: 12px;
  margin-bottom: 15px;
}

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* DETAIL DENGAN PADDING INTERNAL */
.card-details {
  padding: 0 10px;
  color: var(--dark);
  font-size: 0.95rem;
  line-height: 1.6;
  flex-grow: 1;
  margin-bottom: 15px;
}

.card-details p {
  margin-bottom: 8px;
}

/* BUTTON SEPERTI RESCUE */
.btn-selengkapnya {
  display: block;
  text-align: center;
  padding: 12px;
  background-color: var(--dark);
  color: white;
  font-weight: 600;
  text-decoration: none;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.3s;
  font-size: 0.95rem;
}

.btn-selengkapnya:hover {
  background-color: #4a3b2f;
}

/* --- Modal Fade Pop Transition --- */
.fade-pop-enter-active, .fade-pop-leave-active {
  transition: all 0.3s ease;
}

.fade-pop-enter-from {
  opacity: 0;
  transform: translateY(15px) scale(0.97);
}

.fade-pop-leave-to {
  opacity: 0;
  transform: translateY(15px) scale(0.97);
}

/* --- Responsiveness --- */
@media (max-width: 768px) {
  .filter-controls-group {
    flex-direction: column;
    align-items: stretch;
  }
  
  .search-input-center {
    justify-content: stretch;
  }
  
  .select-field {
    max-width: 100%;
  }
  
  .button-report {
    align-self: flex-end;
  }
  
  .search-page-container {
    padding: 20px;
  }
  
  .page-title {
    margin-left: 0;
    text-align: center;
  }
  
  .results-grid {
    padding: 0 15px;
  }
}
</style>