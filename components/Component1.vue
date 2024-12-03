<template>
  <div class="slider-container">
    <!-- Blurred Background -->
    <div
      class="blurred-background"
      :style="{
        backgroundImage: `url(${slides[currentIndex].image})`,
      }"
    ></div>

    <!-- Slider -->
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
          <button class="content-button">{{ slide.buttonText }}</button>
        </div>
      </div>

      <!-- Arrows -->
<button
  class="arrow left"
  :disabled="currentIndex === 0"
  :class="{ disabled: currentIndex === 0 }"
  @click="prevSlide"
>
  ‹
</button>
<button
  class="arrow right"
  :disabled="currentIndex === slides.length - 1"
  :class="{ disabled: currentIndex === slides.length - 1 }"
  @click="nextSlide"
>
  ›
</button>
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
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Bireysel/Banner/Kampanya/8640/banner.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Bireysel/Banner/Kampanya/8142/biogrenci_2011-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/v2-dyson-pasaj-hero.jpg?1732889888000",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/PASAJDA-ONE-CIKANLAR-hero-banner-web.jpg?1732890523000",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/teknolojik-urun-hero-banner-xweb.jpg?1732890182000",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/r1-smarthome-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/r2-ssport-122024pasaj-hero.jpg?1732863384000",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/r4-fkok-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/dt-iPhone16-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/12taksit-may-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/ak-logosuz-pasaj-hero.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/Pasaj_iPhone-hero-banner-web.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/FrsatlarKaps-Hero-Banner-web.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/Herschel-hero-banner-web.jpg",
          buttonText: "İncele",
        },
        {
          image: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Banner/Standart/Pasaj/pasaj-heroxg.jpg",
          buttonText: "İncele",
        },
      ],
    };
  },
  methods: {
    nextSlide() {
      if (this.currentIndex < this.slides.length - 1) {
        this.currentIndex = this.currentIndex + 1;
      }
    },
    prevSlide() {
      if (this.currentIndex > 0) {
        this.currentIndex = this.currentIndex - 1;
      }
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
  max-width: 19200px;
  margin: auto;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  z-index: 0;
}


.slider-container:hover .arrow {
  display: flex; /* Slider üzerinde gezinildiğinde göster */
}

.slider {
  display: flex;
  height: 100%;
  max-height: 1500px;
  transition: transform 0.5s ease-in-out;
  transform: translateX(calc(-100% * var(--current-index)));
  overflow: hidden;
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
  width: 1000px;
  height: 400px;
  object-fit: cover;
  object-position: center;
}

.blurred-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%; /* Slider'ın 1.2 katı yüksekliği */
  background-size: cover;
  background-position: center;
  filter: blur(20px); /* Blur efekti */
  z-index: -1; /* Arka planda durması için */
}



.content {
  position: absolute;
  bottom: 20px;
  left: 20px;
  color: white;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

.content-button {
  position: absolute;
  margin-top: -100px; /* Yukarı taşımak için negatif değer kullanın */
  margin-left: 490px; /* Sağa taşı */
  padding: 15px 55px;
  background: #ffc107;
  border: none;
  color: rgb(40, 85, 172);
  font-weight: bold;
  cursor: pointer;
  border-radius: 8px;
}

.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.7);
  border: none;
  font-size: 36px;
  padding: 20px;
  width: 60px; /* Buton genişliği */
  height: 60px; /* Buton yüksekliği */
  cursor: pointer;
  border-radius: 50%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: none; /* Varsayılan olarak gizle */
  align-items: center;
  justify-content: center;
}

.arrow.left {
  left: 21%;
  background: white;
}

.arrow.right {
  right: 21%;
  background: white;
}

.arrow:disabled,
.arrow.disabled {
  opacity: 0.5; /* Şeffaflık ile pasiflik belirtiliyor */
}

.indicators {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.indicators span {
  display: inline-block;
  width: 30px;
  height: 8px;
  margin: 0 5px;
  background: #ddd;
  border-radius: 25%;
  cursor: pointer;
  margin-bottom: 10px;
}

.indicators span.active {
  background: #ffc107;
}
</style>
