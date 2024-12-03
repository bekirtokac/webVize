<template>
  <div class="search-container" ref="searchContainer">
    <!-- Arama Çubuğu -->
    <div
      class="search-bar"
      :class="{ expanded: isExpanded }"
      @click="expandSearchBar"
    >
    <span class="material-icons-outlined icon">search</span>
      <input
        type="text"
        placeholder="Ürün, marka veya kategori ara"
        v-model="searchQuery"
        @focus="expandSearchBar"
      />
    </div>

    <!-- Genişletilmiş Menü -->
    <div class="expanded-menu" v-if="isExpanded">
  <!-- Üst Bölüm -->
  <div style="background-color: rgb(236, 240, 242);" class="expanded-menu-top">
    <div class="categories">
      <h3>Sana Özel Kategoriler</h3>
      <div class="category-tags">
        <span v-for="(category, index) in specialCategories" :key="index">
          {{ category }}
        </span>
      </div>
    </div>
  </div>

  <!-- Alt Bölüm -->
  <div class="expanded-menu-bottom">
    <div class="popular-searches">
      <h3>Popüler Aramalar</h3>
        <div class="slider-container">
          <div class="slider" :style="sliderStyle">
            <span
              v-for="(search, index) in popularSearches"
              :key="index"
              :class="{ active: activeSearch === index }"
              @click="selectSearch(index)"
              class="slider-item"
              :style="{ width: `${getItemWidth(search)}px` }"
            >
              {{ search }}
            </span>
          </div>
        </div>
      </div>
        <button
          class="slider-btn left"
          @click="slideLeft"
          :disabled="!canSlideLeft"
        >
          &#9664;
        </button>
        <button
          class="slider-btn right"
          @click="slideRight"
          :disabled="!canSlideRight"
        >
          &#9654;
        </button>

        <div class="search-result" v-if="activeSearch !== null">
          <div class="result-container">
            <!-- Görsel ve Metin Yan Yana Kısım -->
            <div class="image-text-container">
              <img
                :src="images[activeSearch]"
                alt="Ürün görseli"
                class="result-image"
              />
              <div class="text-container">
                <div class="details-price">
                  <div class="description">
                    {{ updatedProductDetails[activeSearch] }}
                  </div>
                  <div class="price">
                    {{ prices[activeSearch] }}
                    <span class="currency">TL</span>
                  </div>
                </div>
              </div>
            </div>
            <div class="show-all-wrapper">
              <a href="#" class="show-all">Tüm {{ popularSearches[activeSearch] }} göster</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      updatedProductDetails: [
        "Goldmaster Boss GM-8192 10 in 1 Erkek Bakım Seti",
        "Xiaomi S28D 5W IP67 Taşınabilir Bluetooth Hoparlör",
        "Npo Array Kablo, Makyaj ve Aksesuar Organizer Çantası",
        "PLM Jima 13-14 İnç Notebook Çantası",
        "Varta Energy 5000 mAh Taşınabilir Şarj Cihazı",
        "Termos - Daphnela LED Sıcaklık Gösterge Termos",
        "Spor - Dizi - Film Yayın Paketleri"
      ],
      isExpanded: false,
      searchQuery: "",
      activeSearch: 0,
      specialCategories: [
        "Playstation 5 Pro",
        "iPhone 16",
        "Hediye Çeklerim",
        "Sana Özel Teklifler",
      ],
      images: [
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00CR5S/1-1668684428893/1-1668684428893_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00NICV/2024612110-00NICV-1/2024612110-00NICV-1_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00HWDQ/00HWDQ-16/00HWDQ-16_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00JSYQ/00JSYQ-1/00JSYQ-1_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00LUBL/00LUBL-1/00LUBL-1_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00JF95/00JF95-1/00JF95-1_70x53.png",
        "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/0098C2/202441144-0098C2-1/202441144-0098C2-1_70x53.png",
      ],
      prices: [
        "860.23",
        "799",
        "219",
        "329",
        "599",
        "400",
        "130",
      ],
      popularSearches: [
        "Tıraş Makineleri",
        "Bluetooth Hoparlörler",
        "Çantalar",
        "Laptop Çantaları",
        "Taşınabilir Şarj Cihazları",
        "Termos",
        "Spor - Dizi - Film Yayın Paketleri",
      ],
      currentSlide: 0,
      itemWidths: [],
      visibleWidth: 663,
    };
  },
  computed: {
    totalWidth() {
      return this.itemWidths.reduce((sum, width) => sum + width, 0);
    },
    sliderStyle() {
      const translateX = this.itemWidths
        .slice(0, this.currentSlide)
        .reduce((sum, width) => sum + width, 0);
      return {
        transform: `translateX(-${translateX}px)`,
        width: `${this.totalWidth}px`,
      };
    },
    canSlideLeft() {
      return this.currentSlide > 0;
    },
    canSlideRight() {
      const visibleWidth = this.itemWidths
        .slice(this.currentSlide)
        .reduce((sum, width) => sum + width, 0);
      return visibleWidth > this.visibleWidth;
    },
  },
  methods: {
    selectSearch(index) {
      this.activeSearch = index;
    },
    expandSearchBar() {
      this.isExpanded = true;
    },
    collapseSearchBar() {
      this.isExpanded = false;
      this.activeSearch = 0;
    },
    handleClickOutside(event) {
      const searchContainer = this.$refs.searchContainer;
      if (searchContainer && !searchContainer.contains(event.target)) {
        this.collapseSearchBar();
      }
    },
    slideLeft() {
      if (this.canSlideLeft) {
        this.currentSlide--;
      }
    },
    slideRight() {
      if (this.canSlideRight) {
        this.currentSlide++;
      }
    },
    getItemWidth(search) {
      const charWidth = 8;
      return search.length * charWidth + 30;
    },
  },
  mounted() {
    this.itemWidths = this.popularSearches.map(this.getItemWidth);
    document.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    document.removeEventListener("click", this.handleClickOutside);
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
@import url("https://fonts.googleapis.com/icon?family=Material+Icons+Outlined");

.search-container {
  position: relative;
  width: 663px;
  height: 400px;
  margin: auto;
  font-family: 'Poppins', sans-serif;
  display: flex;
  flex-direction: column;
}

.search-bar {
  display: flex;
  align-items: center;
  padding: 10px 15px;
  border: 1px solid #ddd;
  border-radius: 10px;
  background-color:rgb(236, 240, 242);
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.show-all {
  display: inline-block; /* Padding'in düzgün çalışması için */
  padding: 10px 20px; /* Üst-alt: 10px, Sağ-sol: 20px */
  text-decoration: none; /* Alt çizgiyi kaldırmak için */
  color: rgb(40, 85, 172);
}

.show-all-wrapper {
  margin-top: 0px;
  background-color: white; /* Beyaz arka plan */
  padding: 21px 0; /* Biraz iç boşluk eklemek için */
  align-items: center;
  justify-content: center;
}

.show-all-wrapper .show-all {
  text-decoration: none;
  color: rgb(40, 85, 172);
  transition: background-color 0.3s ease; /* Hover geçiş animasyonu */
}

.show-all-wrapper .show-all:hover {
  background-color: rgb(236, 240, 242); /* Hover sırasında arka plan rengi */
  border-radius: 5px; /* İsteğe bağlı: köşeleri yuvarlatmak için */
  padding: 10px 20px; /* Hover etkisinde daha belirgin boşluk için */
  width: 94%;
}

.result-image {
  width: 70px;
  height: 53px;
  margin-right: 10px;
  float: left;
}

.image-text-container {
  display: flex;
  align-items: center;
  gap: 10px;
  transition: background-color 0.3s ease; /* Hover geçiş animasyonu */
  height: 75px;
}

.image-text-container:hover {
  background-color: rgb(236, 240, 242); /* Hover sırasında arka plan rengi */
  cursor: pointer; /* Hover sırasında imleç tipi */
  height: 75px;
}

.result-details {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.details-price {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  width: 100%;
  flex-wrap: wrap;
  gap: 10px;
}

.description {
  font-size: 14px;
  color: #333;
}

.search-bar.expanded {
  background-color: rgb(236, 240, 242); /* Sarı renk ile değiştirildi */
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  border-color: rgb(236, 240, 242); /* Sarı renk ile uyumlu hale getirildi */
}

.search-bar .material-icons-outlined.icon {
  background-color: rgb(236, 240, 242);
  margin-right: 10px;
  color: #888;
}

.search-bar input {
  background-color: rgb(236, 240, 242);
  flex: 1;
  border: none;
  background: transparent;
  outline: none;
  font-size: 16px;
  color: rgb(142, 159, 173); 
}

.expanded-menu {  
  border: 1px solid #ddd;
  border-top: none;
  border-radius: 0 0 10px 10px;
  background-color: rgb(236, 240, 242); /* Sarı renk */
  flex-grow: 1;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.expanded-menu-bottom {
  background-color: white; /* Beyaz arka plan */
}

.popular-searches {
  padding-top: 3%;
  padding-left: 2%;
  margin-bottom: 20px;
  background-color: white; /* Beyaz arka plan */
}


.categories,
.popular-searches {
  padding-left: 2%;
  margin-bottom: 20px;
}

.categories h3,
.popular-searches h3 {
  padding-left: 1%;
  margin-bottom: 10px;
  font-size: 12px;
  color: rgb(142, 159, 173);
  font-weight: 600;
}

.category-tags span,
.slider-item {
  display: inline-block;
  margin: 5px;
  padding: 10px 15px;
  background-color: #f0f0f0;
  border-radius: 25px;
  font-size: 14px;
  color: #333;
  cursor: pointer;
  text-align: center;
  transition: all 0.3s;
  white-space: nowrap;
}

.category-tags span:hover,
.slider-item.active {
  background-color: rgb(40, 85, 172);
  color: white;
}

.category-tags span {
  display: inline-block;
  margin: 5px;
  padding: 10px 15px;
  background-color: white; /* Arka planı beyaz yap */
  border: 1px solid #ddd; /* İsteğe bağlı, kenarlık eklemek için */
  border-radius: 25px;
  font-size: 14px;
  color: #333; /* Yazı rengi */
  cursor: pointer;
  text-align: center;
  transition: all 0.3s;
  white-space: nowrap;
}

.category-tags span:hover {
  background-color: rgb(40, 85, 172); /* Hover rengi (isteğe bağlı) */
  color: white;
}
.price {
  padding-left: 20px;
  font-size: 22px;
  color: rgb(95, 107, 118);
  font-weight: bold;
  display: flex;
  gap: 2px;
  align-items: center;
}

.currency {
  font-size: 12px;
  vertical-align: top;
  line-height: 1;
}

.slider-container {
  overflow: hidden;
  position: relative;
  width: 100%;
  display: flex;
  align-items: center;
}

.slider {
  display: flex;
  transition: transform 0.3s ease;
}

.slider-btn {
  position: absolute;
  top: 61%;
  transform: translateY(-50%);
  background-color: rgb(236, 240, 242);
  border: 1px solid #ddd;
  border-radius: 50%;
  padding: 5px 10px;
  cursor: pointer;
  font-size: 18px;
}

.slider-btn.left {
  left: 0%;
}

.slider-btn.right {
  right: 0%;
}

.slider-btn:disabled {
  pointer-events: none;
  opacity: 0.5;
}
</style>
