<template>
  <div class="popular-brands-container">
    <div class="header">
      <h2>Popüler Markalar</h2>
      <a href="#" class="view-all">Tüm Markalar</a>
    </div>
    <div class="brands-slider">
      <!-- Sol ok -->
      <button class="arrow left" @click="prevSlide">‹</button>

      <!-- Markalar -->
      <div class="brands-list">
        <div
          class="brand-item"
          v-for="(brand, index) in visibleBrands"
          :key="index"
        >
          <img :src="brand.logo" :alt="brand.name" />
        </div>
      </div>

      <!-- Sağ ok -->
      <button class="arrow right" @click="nextSlide">›</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      brands: [
        { name: "Philips", logo: "https://via.placeholder.com/100x50?text=Philips" },
        { name: "Sony", logo: "https://via.placeholder.com/100x50?text=Sony" },
        { name: "Lenovo", logo: "https://via.placeholder.com/100x50?text=Lenovo" },
        { name: "JBL", logo: "https://via.placeholder.com/100x50?text=JBL" },
        { name: "Dyson", logo: "https://via.placeholder.com/100x50?text=Dyson" },
        { name: "Casper", logo: "https://via.placeholder.com/100x50?text=Casper" },
        { name: "Braun", logo: "https://via.placeholder.com/100x50?text=Braun" },
        { name: "Realme", logo: "https://via.placeholder.com/100x50?text=Realme" },
        { name: "Arzum", logo: "https://via.placeholder.com/100x50?text=Arzum" },
        { name: "Samsung", logo: "https://via.placeholder.com/100x50?text=Samsung" },
        { name: "Apple", logo: "https://via.placeholder.com/100x50?text=Apple" },
      ],
      startIndex: 0, // Gösterilen markaların başlangıç indeksi
      visibleCount: 9, // Aynı anda gösterilecek marka sayısı
    };
  },
  computed: {
    visibleBrands() {
      return this.brands.slice(
        this.startIndex,
        this.startIndex + this.visibleCount
      );
    },
  },
  methods: {
    nextSlide() {
      if (this.startIndex + this.visibleCount < this.brands.length) {
        this.startIndex++;
      }
    },
    prevSlide() {
      if (this.startIndex > 0) {
        this.startIndex--;
      }
    },
  },
};
</script>

<style scoped>
.popular-brands-container {
  width: 80%; /* Genişliği ekranın %80'i olarak ayarlandı */
  margin: 0 auto; /* Ortalamak için */
  padding: 20px 0;
  background-color: #f9f9f9;
  position: relative;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.header h2 {
  font-size: 24px;
  margin: 0;
}

.header .view-all {
  font-size: 14px;
  color: #007bff;
  text-decoration: none;
}

.header .view-all:hover {
  text-decoration: underline;
}

.brands-slider {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.brands-list {
  display: flex;
  transition: transform 0.3s ease;
}

.brand-item {
  flex: 0 0 auto;
  width: calc(100% / 9 - 10px); /* 9 marka için eşit genişlik */
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 5px; /* Aralarında boşluk */
  border: 1px solid #ddd;
  border-radius: 10px;
  background: white;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
}

.brand-item img {
  max-width: 80%;
  max-height: 60%;
}

.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: #fff;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.arrow.left {
  left: 100px; /* Sol oka daha yakın */
}

.arrow.right {
  right: 100px; /* Sağ oka daha yakın */
}

.arrow:hover {
  background: #007bff;
  color: white;
}
</style>
