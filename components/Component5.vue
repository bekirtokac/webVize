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
        { name: "Braun", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/braun-logo.png?1731801459000" },
        { name: "Siemens", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/siemens-logo.png?1731801459000" },
        { name: "Lenovo", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/lenovo-logo.png?1731801459000" },
        { name: "JBL", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/jbl-logo.png?1731801459000" },
        { name: "Dyson", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/dyson-logo.png?1731801459000" },
        { name: "Casper", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/casper-logo.png?1731801459000" },
        { name: "Realme", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/realme-logo.png?1731801459000" },
        { name: "Arzum", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/arzum-logo.png?1731801459000" },
        { name: "Anker", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/anker-logo.png?1731801459000" },
        { name: "Omix", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/omix-logo.png?1731801459000" },
        { name: "Karaca", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/karaca-logo.png?1731801459000" },
        { name: "Bosch", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/bosch-logo.png?1731801459000" },
        { name: "Vestel", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/vestel-logo.png?1731801459000" },
        { name: "Lego", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/lego-logo.png?1731801459000" },
        { name: "Beko", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/beko-logo.png?1731801459000" },
        { name: "Sony", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/sony-logo.png?1731801459000" },
        { name: "Philips", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/philips-logo.png?1731801459000" },
        { name: "Huawei", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/huawei-logo-2.png?1731801459000" },
        { name: "Mi", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/mi-logo.png?1731801459000" },
        { name: "Samsung", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/samsung-logo.png?1731801459000" },
        { name: "Apple", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/apple-logo.png?1731801459000" },
        { name: "TCL", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/tcl-logo.png?1731801459000" },
        { name: "Karcher", logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/promo/karcher-logo.png?1731801459000" },
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
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");

.popular-brands-container {
  width: 80%;
  margin: 0 auto;
  padding: 20px 0;
  background-color: white;
  position: relative;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.header h2 {
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  font-size: 34px;
  margin: 0;
}

.header .view-all {
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  font-size: 16px;
  color: rgb(40, 85, 172);
  text-decoration: none;
}

.header .view-all:hover {
  text-decoration: underline;
}

.brands-slider {
  padding-left: 0%;
  padding-right: 0%;
  align-items: center;
  justify-content: center;
  width: 98%;
  display: flex;
  position: relative;
  overflow: hidden;
}

.brands-list {
  width: 97%;
  display: flex;
  transition: transform 0.3s ease;
}

.brand-item {
  flex: 0 0 auto;
  width: calc(100% / 9 - 10px);
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 5px;
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
  width: 3%;
  height: 50%;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  font-size: 20px;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.arrow.left {
  left: 1%;
}

.arrow.right {
  right: -1%;
}
</style>
