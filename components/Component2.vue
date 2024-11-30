<template>
  <div class="product-list">
    <h2>En İyi Teklifler</h2>
    <div class="products">
      <div v-for="(product, index) in products" :key="index" class="product-card">
        <!-- Ürün Resmi -->
        <div class="image-container">
          <img :src="product.image" :alt="product.title" />
          <button class="favorite-button">
            <span>♥</span>
          </button>
        </div>

        <!-- Ürün Bilgileri -->
        <div class="product-info">
          <h3>{{ product.title }}</h3>
          <p class="rating">
            <span>⭐ {{ product.rating }}</span>
          </p>
          <div class="tags">
            <span v-for="(tag, tagIndex) in product.tags" :key="tagIndex" class="tag">{{ tag }}</span>
          </div>
          <p class="price">{{ product.price }}</p>
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
          image: "https://via.placeholder.com/150",
          title: "Philips 4K Ambilight TV",
          rating: "5,0",
          tags: ["Alışveriş Kredisi", "Peşine 4 Taksit", "Ücretsiz Kargo"],
          price: "36.999 TL",
        },
        {
          image: "https://via.placeholder.com/150",
          title: "Karcher Elektrikli Süpürge",
          rating: "4,5",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
          price: "2.899 TL",
        },
        {
          image: "https://via.placeholder.com/150",
          title: "Arnica Şarjlı Dik Süpürge",
          rating: "4,8",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
          price: "4.099 TL",
        },
        {
          image: "https://via.placeholder.com/150",
          title: "Xiaomi Redmi 13C",
          rating: "4,3",
          tags: ["Alışveriş Kredisi", "Ücretsiz Kargo", "Hızlı Teslimat"],
          price: "8.998 TL",
        },
      ],
    };
  },
};
</script>

<style scoped>
.product-list {
  padding: 20px;
}

.product-list h2 {
  font-size: 24px;
  margin-bottom: 20px;
  font-weight: bold;
}

.products {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: space-between;
}

.product-card {
  width: 220px;
  background: white;
  border: 1px solid #eee;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
}

.image-container {
  position: relative;
  width: 100%;
  height: 150px;
  background: #f9f9f9;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.favorite-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
  color: #ffcc00;
}

.product-info {
  padding: 10px;
}

.product-info h3 {
  font-size: 16px;
  margin: 10px 0;
  font-weight: bold;
}

.product-info .rating {
  font-size: 14px;
  color: #888;
}

.product-info .tags {
  display: flex;
  gap: 5px;
  margin: 10px 0;
}

.product-info .tags .tag {
  font-size: 12px;
  padding: 5px 10px;
  background: #f4f4f4;
  border-radius: 5px;
}

.product-info .price {
  font-size: 18px;
  font-weight: bold;
  color: #333;
  margin-top: 10px;
}
</style>
