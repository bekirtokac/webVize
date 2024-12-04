<template>
  <div class="product-list">
    <h2></h2>
    <div class="products">
      <div
        v-for="(product, index) in products"
        :key="index"
        class="product-card"
      >
        <!-- Ürün Resmi -->
        <div
          class="image-container"
          @mousedown="startDrag(index, $event)"
          @mousemove="onDrag(index, $event)"
          @mouseup="endDrag"
          @mouseleave="endDrag"
        >
          <template v-if="product.images.length > 1">
            <div class="carousel">
              <img
                :src="product.images[activeImageIndex[index]]"
                :alt="product.title"
              />
              <div class="dots">
                <span
                  v-for="(image, imgIndex) in product.images"
                  :key="imgIndex"
                  :class="{ active: imgIndex === activeImageIndex[index] }"
                  @click="changeImage(index, imgIndex)"
                ></span>
              </div>
            </div>
          </template>
          <template v-else>
            <img :src="product.images[0]" :alt="product.title" />
          </template>
          <button class="favorite-button" @click="toggleFavorite(index)">
            <span v-if="!product.isFavorite">♡</span>
            <span v-else>♥</span>
          </button>
          <div
            v-if="product.title === 'Arnica Şarjlı Dik Süpürge'"
            class="deal-of-the-day"
            style="top: 0; left: 0"
          >
            Günün Teklifleri
          </div>
          <div v-if="index === 3" class="extra-photos">
            <span class="black-circle"></span>
            <span class="white-circle"></span>
          </div>
          <div v-if="index === 0" class="extra-photos">
            <span class="grey-circle"></span>
            <span class="pink-circle"></span>
          </div>
        </div>

        <!-- Ürün Bilgileri -->
        <div class="product-info">
          <h3>{{ product.title }}</h3>
          <p class="rating">
            <template v-if="index === 3">
              <span
                v-for="n in 5"
                :key="n"
                :class="{ 'filled-star': n <= Math.round(product.rating) }"
                >⭐</span
              >
              <span>{{ product.rating }}</span>
            </template>
            <template v-else>
              <span class="empty-placeholder">⠀</span>
            </template>
          </p>
          <div class="tags">
            <span
              v-for="(tag, tagIndex) in product.tags"
              :key="tagIndex"
              class="tag"
              :style="getTagStyle(tag)"
              >{{ tag }}</span
            >
          </div>
          <div class="price-separator"></div>
          <div v-if="index === 0" class="price-container" style="height: 60px">
            <p class="price">
              <span>{{ product.price.split(" ")[0] }}</span>
              <span class="currency">TL</span>
            </p>
            <p class="price-details" style="margin-top: -20px">
              <span
                class="old-price"
                style="
                  text-decoration: line-through;
                  color: grey;
                  margin-right: 10px;
                "
              >
                7.499 TL
              </span>
              <span
                class="discount-info"
                style="color: #00bacf; font-weight: bold"
              >
                400 TL İndirim
              </span>
            </p>
            <p
              class="lowest-price"
              style="color: rgb(0, 153, 0); font-size: 12px; margin-top: -20px"
            >
              Son 30 günün en düşük fiyatı
            </p>
          </div>
          <p v-else class="price">
            <span>{{ product.price.split(" ")[0] }}</span>
            <span class="currency">TL</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          images: [
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125932-00QCEB-1/20241125932-00QCEB-1_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125932-00QCEB-2/20241125932-00QCEB-2_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125932-00QCEB-3/20241125932-00QCEB-3_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125933-00QCEB-4/20241125933-00QCEB-4_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125933-00QCEB-5/20241125933-00QCEB-5_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QCEB/20241125933-00QCEB-6/20241125933-00QCEB-6_600x450.png?1731801459000",
          ],
          title: "Hometech Alfa 11BT 128 GB 10.95 inç Tablet",
          rating: "5,0",
          tags: ["Alışveriş Kredisi", "Peşine 4 Taksit", "Ücretsiz Kargo"],
          price: "40.999 TL",
          isFavorite: false,
        },
        {
          images: [
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00ANHA/1-1646228159484/1-1646228159484_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00ANHA/2-1646228196396/2-1646228196396_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00ANHA/3-1646229116782/3-1646229116782_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00ANHA/4-1646229146682/4-1646229146682_600x450.png?1731801459000",
          ],
          title: "Arnica ET 11201 Süpürge E- Max Şarjlı Dik Süpürge",
          rating: "4,8",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
          price: "4.449 TL",
          isFavorite: false,
        },
        {
          images: [
            "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/pasaj/crop/cg/00BLHL/1-1655367692491/1-1655367692491_250x188.png?1731801459000",
          ],
          title: "Karcher KWD 1 W V-12/2/18 Islak/Kuru Elektrikli Süpürge",
          rating: "4,5",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
          price: "3.099 TL",
          isFavorite: false,
        },

        {
          images: [
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QH1H/20241191530-00QH1H-1/20241191530-00QH1H-1_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QH1H/20241191530-00QH1H-2/20241191530-00QH1H-2_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QH1H/20241191531-00QH1H-3/20241191531-00QH1H-3_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QH1H/20241191531-00QH1H-4/20241191531-00QH1H-4_600x450.png?1731801459000",
            "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00QH1H/20241191532-00QH1H-5/20241191532-00QH1H-5_600x450.png?1731801459000",
          ],
          title: "Xiaomi Redmi 13C 8 GB Ram 256 GB",
          rating: "4,3",
          tags: ["Alışveriş Kredisi", "Ücretsiz Kargo", "Hızlı Teslimat"],
          price: "8.799 TL",
          isFavorite: false,
        },
      ],
      activeImageIndex: {},
      isDragging: false,
      startX: 0,
    };
  },
  created() {
    this.products.forEach((_, index) => {
      this.activeImageIndex[index] = 0;
    });
  },
  methods: {
    toggleFavorite(index) {
      this.products[index].isFavorite = !this.products[index].isFavorite;
    },
    getTagStyle(tag) {
      switch (tag) {
        case "Alışveriş Kredisi":
        case "Faturana Ek 36 Taksit":
          return { backgroundColor: "rgba(0, 233, 10, 0.1)" };
        case "Peşine 4 Taksit":
        case "Peşine 6 Taksit":
          return { backgroundColor: "rgb(229, 248, 255)" };
        case "Ücretsiz Kargo":
        case "Hızlı Teslimat":
          return { backgroundColor: "rgb(253, 247, 231)" };
        default:
          return {};
      }
    },
    changeImage(productIndex, imageIndex) {
      this.activeImageIndex[productIndex] = imageIndex;
    },
    startDrag(index, event) {
      this.isDragging = true;
      this.startX = event.clientX;
    },
    onDrag(index, event) {
      if (this.isDragging) {
        const currentX = event.clientX;
        const diff = currentX - this.startX;

        if (diff > 50) {
          // Sağa doğru kaydırıldıysa
          this.activeImageIndex[index] =
            (this.activeImageIndex[index] + 1) %
            this.products[index].images.length;
          this.startX = currentX;
        } else if (diff < -50) {
          // Sola doğru kaydırıldıysa
          this.activeImageIndex[index] =
            (this.activeImageIndex[index] -
              1 +
              this.products[index].images.length) %
            this.products[index].images.length;
          this.startX = currentX;
        }
      }
    },
    endDrag() {
      this.isDragging = false;
    },
  },
};
</script>

@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
<style scoped>
.product-list {
  padding: 20px;
}

.product-list h2 {
  padding-left: 15%;
  font-family: "Poppins", sans-serif;
  font-size: 34px;
  margin-bottom: 20px;
  font-weight: bold;
}

.products {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.product-card {
  width: 300px;
  height: 500px;
  background: white;
  border: 1px solid #eee;
  border-radius: 10px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: border-color 0.3s;
}

.product-card:hover {
  border-color: #ffcc00;
}

.image-container {
  position: relative;
  width: 280px;
  height: 300px;
  background: #ffffff;
  cursor: grab;
  overflow: hidden;
}

.image-container img {
  width: 280px;
  height: 210px;
  object-fit: cover;
  user-select: none;
  pointer-events: none;
}

.extra-photos {
  position: absolute;
  bottom: 10px;
  left: 10px;
  background-color: white;
  border: 1px solid #eee;
  border-radius: 5px;
  padding: 2px 5px;
  display: flex;
  align-items: center;
  gap: 5px;
}

.extra-photos .black-circle {
  width: 10px;
  height: 10px;
  background-color: #000;
  border-radius: 50%;
}

.extra-photos .white-circle {
  width: 10px;
  height: 10px;
  background-color: #fff;
  border-radius: 50%;
}
.extra-photos .grey-circle {
  width: 10px;
  height: 10px;
  background-color: #818085;
  border-radius: 50%;
}

.extra-photos .pink-circle {
  width: 10px;
  height: 10px;
  background-color: #c8a2c8;
  border-radius: 50%;
}

.extra-photos .photo-count {
  font-family: "Poppins", sans-serif;
  font-size: 12px;
  font-weight: bold;
  color: #333;
}

.carousel {
  position: relative;
  width: 100%;
  height: 100%;
}

.carousel .dots {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 5px;
}

.carousel .dots span {
  width: 8px;
  height: 8px;
  background: #ccc;
  border-radius: 50%;
  cursor: pointer;
}

.carousel .dots span.active {
  background: #333;
}

.favorite-button {
  font-family: "Poppins", sans-serif;
  position: absolute;
  top: 10px;
  right: 10px;
  background: transparent;
  border: none;
  font-size: calc(20px * 2);
  cursor: pointer;
  color: #ffcc00;
  cursor: pointer;
  color: #ffcc00;
}

.deal-of-the-day {
  font-family: "Poppins", sans-serif;
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgb(0, 186, 252);
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 12px;
  font-weight: bold;
}
/**fotoğrafın altı */
.product-info {
  padding: 10px;
  font-family: "Poppins", sans-serif;
  font-size: 16px;
}
/**yazı */
.product-info h3 {
  font-family: "Poppins", sans-serif;
  font-size: 16px;
  margin: 10px 0;
  font-weight: bold;
}

.rating {
  font-family: "Poppins", sans-serif;
  font-size: 14px;
  color: #888;
  display: flex;
  align-items: center;
  gap: 5px;
  min-height: 20px; /* Yıldızların yüksekliği kadar bir minimum yükseklik ekledik */
}

.rating .empty-placeholder {
  visibility: hidden; /* Boşluğu oluşturuyor, ancak görünmez yapıyor */
}

.rating .filled-star {
  color: #ffd700;
}

.product-info .tags {
  display: flex;
  gap: 5px;
  margin: 10px 0;
}

.product-info .tags .tag {
  font-family: "Poppins", sans-serif;
  font-size: 60%;
  padding: 5px 10px;
  background: #f4f4f4;
  border-radius: 5px;
  color: rgb(95, 107, 118);
}

.price-separator {
  width: calc(100% + 20px);
  height: 1px;
  background-color: rgb(236, 240, 242);
  margin: 10px -10px;
}

.product-info .price {
  font-family: "Poppins", sans-serif;
  font-size: 18px;
  font-weight: bold;
  color: rgb(40, 85, 172);
  margin-top: 10px;
  position: relative;
  display: inline-block;
}

.product-info .price .currency {
  font-family: "Poppins", sans-serif;
  font-size: 70%;
  position: absolute;
  top: -5px;
  right: -20px;
}
</style>
