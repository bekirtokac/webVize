<template>
  <div class="special-deals-container">
    <h2>Kaçırılmayacak Fırsatlar</h2>
    <div class="slider">
      <!-- Sol Ok -->
      <button class="arrow left" @click="prevSlide">‹</button>

      <!-- Slider Kartları -->
      <div class="slides">
        <div class="slide" v-for="(deal, index) in visibleDeals" :key="index"
          :style="{ backgroundImage: `url(${deal.background})` }">
          <div class="slide-content">
            <h3>{{ deal.title }}</h3>
            <p>{{ deal.description }}</p>
          </div>
        </div>
      </div>

      <!-- Sağ Ok -->
      <button class="arrow right" @click="nextSlide">›</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      deals: [
        {
          title: "400 TL Bonus fırsatı!",
          description: "20.000 TL üzeri alışverişlerinizde geçerli fırsatı kaçırmayın.",
          background: "https://via.placeholder.com/300x500?text=Bonus+Fırsatı",
        },
        {
          title: "QNB GO Kredi Kartı",
          description: "İlk işlemine 500 TL ParaPuan kazanın!",
          background: "https://via.placeholder.com/300x500?text=QNB+GO",
        },
        {
          title: "Maximum Kart’a başvur",
          description: "Ayda 20.000 TL’yi aşan MaxiPuan kazan!",
          background: "https://via.placeholder.com/300x500?text=Maximum+Kart",
        },
        {
          title: "HangiKredi Faizsiz Finans",
          description: "0% faizli 45.000 TL nakit avantajı ile ihtiyacını erteleme!",
          background: "https://via.placeholder.com/300x500?text=HangiKredi",
        },
      ],
      currentIndex: 0, // Mevcut slide indeksi
      visibleCount: 3, // Aynı anda görünen kart sayısı
    };
  },
  computed: {
    visibleDeals() {
      return this.deals.slice(this.currentIndex, this.currentIndex + this.visibleCount);
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
  flex: 1 1 calc(25% - 20px);
  /* Her kart eşit genişlikte */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 10px;
  color: white;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  min-height: 300px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.slide-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
}

.slide-content p {
  font-size: 14px;
}

.arrow {
  position: absolute;
  top: 50%;
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
}

.arrow.left {
  left: -20px;
}

.arrow.right {
  right: -20px;
}

.arrow:hover {
  background: #007bff;
  color: white;
}
</style>
