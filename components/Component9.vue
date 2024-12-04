<template>
  <div class="special-deals-container">
    <h2 class="header">Kaçırılmayacak Fırsatlar</h2>
    <div class="slider">
      <!-- Sol Ok -->
      <button
        class="arrow left"
        @click="prevSlide"
        :class="{ disabled: currentIndex === 0 }"
      >
        ‹
      </button>

      <!-- Slider Kartları -->
      <div class="slides">
        <div class="slide" v-for="(deal, index) in visibleDeals" :key="index">
          <!-- Görsel -->
          <img :src="deal.image" :alt="deal.title" class="slide-image" />
          <!-- İçerik -->
        </div>
      </div>

      <!-- Sağ Ok -->
      <button
        class="arrow right"
        @click="nextSlide"
        :class="{ disabled: currentIndex + visibleCount >= deals.length }"
      >
        ›
      </button>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      deals: [
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/bonusbf2611-KF.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/qnb-kasim-KF.webp", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/isbnk20k-KF.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/hk45k-KF.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/r1-pacunku-kkff.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/fr1-go4-KFx.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/Herschel-xkfxf.jpg", // Görsel yolu
        },
        {
          image:
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/firsat/web/r1-tvpluspro-KF.jpg", // Görsel yolu
        },
      ],
      currentIndex: 0, // Şu anda gösterilen slide
      visibleCount: 4, // Aynı anda kaç slide gösterileceği
    };
  },
  computed: {
    visibleDeals() {
      return this.deals.slice(
        this.currentIndex,
        this.currentIndex + this.visibleCount
      );
    },
  },
  methods: {
    nextSlide() {
      if (this.currentIndex + this.visibleCount < this.deals.length) {
        this.currentIndex++;
      }
    },
    prevSlide() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");

.header {
  font-family: "Poppins", sans-serif;
  font-weight: 600;
  font-size: 34px;
  margin: 0;
}

.special-deals-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.special-deals-container h2 {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.slider {
  display: flex;
  align-items: center;
  position: relative;
}

.slides {
  display: flex;
  overflow: hidden;
  gap: 20px;
  flex-grow: 1;
}

.slide {
  flex: 1 1 calc(33% - 20px);
  /* 3 slide yan yana */
  border-radius: 10px;
  background: #f4f4f4;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.slide img {
  width: 100%;
  height: 420px;
  object-fit: cover;
}

.slide-content {
  padding: 15px;
  text-align: center;
}

.slide-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #007bff;
}

.slide-content p {
  font-size: 14px;
  color: #555;
}

.arrow {
  position: absolute;
  top: 40%;
  transform: translateY(-50%);
  background: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
  font-size: 20px;
  color: #333;
  transition: opacity 0.3s ease, cursor 0.3s ease;
}

.arrow.disabled {
  opacity: 0.4;
  /* Soluk hale getir */
  pointer-events: none;
  /* Tıklanamaz yap */
  cursor: not-allowed;
  /* İşaretçi stilini değiştir */
}

.arrow.left {
  left: -20px;
}

.arrow.right {
  right: -20px;
}
</style>
