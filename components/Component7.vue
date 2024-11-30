<template>
  <div class="new-products-container">
    <h2>Pasaj'ın Yenileri</h2>
    <div class="products-grid">
      <div class="product-card" v-for="(product, index) in products" :key="index">
        <!-- Favori Butonu -->
        <div class="favorite">
          <i class="icon-heart">❤️</i>
        </div>

        <!-- Ürün Görseli -->
        <div class="product-image">
          <img :src="product.image" :alt="product.name" />
        </div>

        <!-- Ürün Adı -->
        <div class="product-info">
          <h4>{{ product.name }}</h4>

          <!-- Etiketler -->
          <div class="tags">
            <span v-for="(tag, i) in product.tags" :key="i" class="tag">
              {{ tag }}
            </span>
          </div>

          <!-- Fiyat -->
          <div class="price">{{ product.price }} TL</div>
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
          name: "Karcher KWD 1 W V-12/2/18 Islak/Kuru Elektrikli Süpürge",
          image: "https://via.placeholder.com/150", // Örnek görsel
          price: "2.899",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
        },
        {
          name: "Arnica Mila ET14440 Toz Torbasız Elektrikli Süpürge",
          image: "https://via.placeholder.com/150", // Örnek görsel
          price: "4.489",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
        },
        {
          name: "Biggdesign Cats 3'lü Valiz Seti",
          image: "https://via.placeholder.com/150", // Örnek görsel
          price: "2.559",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
        },
        {
          name: "Lecoo WS216 Kablosuz 1600DPI 7 Tuşlu Optik Mouse",
          image: "https://via.placeholder.com/150", // Örnek görsel
          price: "299",
          tags: ["Faturana Ek 36 Taksit", "Peşine 6 Taksit", "Ücretsiz Kargo"],
        },
      ],
    };
  },
};
</script>

<style scoped>
.new-products-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.new-products-container h2 {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.products-grid {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: space-between;
}

.product-card {
  background: white;
  border: 1px solid #ddd;
  border-radius: 10px;
  width: calc(25% - 15px);
  /* Her satırda 4 ürün gösterilecek */
  padding: 15px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.favorite {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 20px;
  color: #ff0000;
  cursor: pointer;
}

.product-image {
  text-align: center;
  margin-bottom: 15px;
}

.product-image img {
  max-width: 100%;
  max-height: 150px;
  object-fit: contain;
}

.product-info h4 {
  font-size: 16px;
  color: #555;
  margin-bottom: 10px;
  text-align: center;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 5px;
  margin-bottom: 10px;
}

.tag {
  background: #f8f9fa;
  color: #007bff;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 12px;
  border: 1px solid #007bff;
}

.price {
  font-size: 20px;
  color: #222;
  font-weight: bold;
  text-align: center;
}
</style>
