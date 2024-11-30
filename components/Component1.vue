<template>
  <div class="slider-container">
    <div class="slider">
      <!-- Slider Items -->
      <div
        v-for="(slide, index) in slides"
        :key="index"
        class="slide"
        :class="{ active: currentIndex === index }"
      >
        <img :src="slide.image" :alt="slide.title" />
        <div class="content">
          <h2>{{ slide.title }}</h2>
          <p>{{ slide.description }}</p>
          <button>{{ slide.buttonText }}</button>
        </div>
      </div>

      <!-- Arrows -->
      <button class="arrow left" @click="prevSlide">‹</button>
      <button class="arrow right" @click="nextSlide">›</button>
    </div>

    <!-- Indicators -->
    <div class="indicators">
      <span
        v-for="(slide, index) in slides"
        :key="index"
        :class="{ active: currentIndex === index }"
        @click="goToSlide(index)"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0, // Aktif slide'ı tutar
      slides: [
        {
          image: "https://via.placeholder.com/800x400?text=Slide+1",
          title: "PS5 Pro",
          description: "Şimdi satışta! Peşin fiyatına 6 taksit.",
          buttonText: "İncele",
        },
        {
          image: "https://via.placeholder.com/800x400?text=Slide+2",
          title: "Kampanya 2",
          description: "Sınırlı süreli indirimler!",
          buttonText: "Detaylar",
        },
        {
          image: "https://via.placeholder.com/800x400?text=Slide+3",
          title: "Kampanya 3",
          description: "Kaçırılmayacak fırsatlar!",
          buttonText: "Hemen Al",
        },
      ],
    };
  },
  methods: {
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.slides.length;
    },
    prevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.slides.length) % this.slides.length;
    },
    goToSlide(index) {
      this.currentIndex = index;
    },
  },
};
</script>

<style scoped>
.slider-container {
  position: relative;
  width: 100%;
  max-width: 800px;
  margin: auto;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.slider {
  display: flex;
  transition: transform 0.5s ease-in-out;
  transform: translateX(calc(-100% * var(--current-index)));
}

.slide {
  min-width: 100%;
  display: none;
  flex-shrink: 0;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative;
}

.slide.active {
  display: flex;
}

.slide img {
  width: 100%;
  height: auto;
  object-fit: cover;
}

.content {
  position: absolute;
  bottom: 20px;
  left: 20px;
  color: white;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

.content button {
  margin-top: 10px;
  padding: 10px 20px;
  background: #ffc107;
  border: none;
  color: #000;
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
}

.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.7);
  border: none;
  font-size: 24px;
  padding: 10px;
  cursor: pointer;
  border-radius: 50%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

.arrow.left {
  left: 10px;
}

.arrow.right {
  right: 10px;
}

.indicators {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.indicators span {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 0 5px;
  background: #ddd;
  border-radius: 50%;
  cursor: pointer;
}

.indicators span.active {
  background: #ffc107;
}
</style>
