<template>
  <div class="search-container" ref="searchContainer">
    <!-- Arama Çubuğu -->
    <div
      class="search-bar"
      :class="{ expanded: isExpanded }"
      @click="expandSearchBar"
    >
      <i class="icon">🔍</i>
      <input
        type="text"
        placeholder="Ürün, marka veya kategori ara"
        v-model="searchQuery"
        @focus="expandSearchBar"
      />
    </div>

    <!-- Genişletilmiş Menü -->
    <div class="expanded-menu" v-if="isExpanded">
      <div class="categories">
        <h3>Sana Özel Kategoriler</h3>
        <div class="category-tags">
          <span v-for="(category, index) in specialCategories" :key="index">
            {{ category }}
          </span>
        </div>
      </div>

      <div class="popular-searches">
        <h3>Popüler Aramalar</h3>
        <div class="search-tags">
          <span
            v-for="(search, index) in popularSearches"
            :key="index"
            :class="{ active: activeSearch === index }"
            @click="selectSearch(index)"
          >
            {{ search }}
          </span>
        </div>
        <div class="search-result" v-if="activeSearch !== null">
          <p><strong>{{ popularSearches[activeSearch] }}:</strong> Goldmaster Boss GM-8192 10 in 1 Erkek Bakım Seti</p>
          <p class="price">860,23 TL</p>
          <a href="#" class="show-all">Tüm {{ popularSearches[activeSearch] }} göster</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isExpanded: false, // Search bar genişleme durumu
      searchQuery: "", // Arama çubuğundaki metin
      activeSearch: null, // Aktif popüler arama
      specialCategories: ["Playstation 5 Pro", "iPhone 16", "Hediye Çeklerim", "Sana Özel Teklifler"], // Özel kategoriler
      popularSearches: ["Tıraş Makineleri", "Bluetooth Hoparlörler", "Çantalar", "Laptop Çantaları", "Powerbankler"], // Popüler aramalar
    };
  },
  methods: {
    expandSearchBar() {
      this.isExpanded = true;
    },
    collapseSearchBar() {
      this.isExpanded = false;
      this.activeSearch = null; // Popüler aramaları sıfırlar
    },
    selectSearch(index) {
      this.activeSearch = index;
    },
    handleClickOutside(event) {
      const searchContainer = this.$refs.searchContainer;
      if (searchContainer && !searchContainer.contains(event.target)) {
        this.collapseSearchBar();
      }
    },
  },
  mounted() {
    document.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    document.removeEventListener("click", this.handleClickOutside);
  },
};
</script>

<style scoped>
/* Genel Container */
.search-container {
  position: relative;
  max-width: 600px;
  margin: auto;
}

/* Dar Arama Çubuğu */
.search-bar {
  display: flex;
  align-items: center;
  padding: 10px 15px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background-color: #f7f9fc;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.search-bar.expanded {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  border-color: #ccc;
}

.search-bar i.icon {
  margin-right: 10px;
  color: #888;
}

.search-bar input {
  flex: 1;
  border: none;
  background: transparent;
  outline: none;
  font-size: 16px;
  color: #666;
}

/* Genişletilmiş Menü */
.expanded-menu {
  border: 1px solid #ddd;
  border-top: none;
  border-radius: 0 0 10px 10px;
  background-color: #fff;
  padding: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.categories,
.popular-searches {
  margin-bottom: 20px;
}

.categories h3,
.popular-searches h3 {
  margin-bottom: 10px;
  font-size: 14px;
  color: #333;
  font-weight: bold;
}

.category-tags span,
.search-tags span {
  display: inline-block;
  margin: 5px;
  padding: 5px 10px;
  background-color: #f0f0f0;
  border-radius: 20px;
  font-size: 12px;
  color: #666;
  cursor: pointer;
  transition: background 0.3s;
}

.category-tags span:hover,
.search-tags span.active {
  background-color: #007bff;
  color: white;
}

.search-result {
  margin-top: 15px;
  font-size: 14px;
}

.search-result p {
  margin: 5px 0;
}

.search-result .price {
  color: #007bff;
  font-weight: bold;
  font-size: 16px;
}

.search-result .show-all {
  display: block;
  margin-top: 10px;
  color: #007bff;
  text-decoration: none;
  font-size: 14px;
}

.search-result .show-all:hover {
  text-decoration: underline;
}
</style>
