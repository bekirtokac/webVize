<template>
  <div class="product-detail-container">
    <!-- Sol: Ürün Görseli -->
    <div class="product-image">
      <img :src="product.image" :alt="product.name" />
    </div>

    <!-- Sağ: Ürün Detayları -->
    <div class="product-info">
      <h5>{{ product.brand }}</h5>
      <h1>{{ product.name }}</h1>
      <p class="review">
        Henüz yorum yok <a href="#">Yorum Yaz</a>
      </p>

      <div class="installment">
        <a href="#">{{ product.installmentText }}</a>
      </div>

      <div class="seller" style="background-color: #eff5ff;">
        <p>Ücretsiz Kargo</p>
        <div class="seller-info">
          <input type="radio" id="seller" name="seller" checked />
          <label for="seller">{{ product.seller.name }}</label>
          <span class="rating">{{ product.seller.rating }}</span>
        </div>
        <div class="price">{{ product.price }} TL</div>
        <p class="shipping-time">3 iş gününde kargoda</p>
      </div>

      <button class="add-to-cart">Sepete Ekle</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        image: "https://via.placeholder.com/300x400", // Örnek ürün görseli
        brand: "Pro Plan",
        name: "Pro Plan Medium Adult Somonlu Hassas Yetişkin Köpek Maması 14 Kg",
        installmentText: "Peşin Fiyatına 6 Taksit!",
        seller: {
          name: "KUZEY PAZARLAMA",
          rating: "10.0",
        },
        price: "3.098,90",
      },
    };
  },
};
</script>

<style scoped>
.product-detail-container {
  display: flex;
  gap: 20px;
  padding: 20px;
  background-color: #fff;
  max-width: 1200px;
  margin: auto;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.product-image {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.product-image img {
  max-width: 100%;
  border-radius: 10px;
}

.product-info {
  flex: 2;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.product-info h5 {
  font-size: 18px;
  color: #555;
  margin-bottom: 10px;
}

.product-info h1 {
  font-size: 24px;
  color: #222;
  margin-bottom: 20px;
}

.product-info .review {
  font-size: 14px;
  color: #888;
  margin-bottom: 10px;
}

.product-info .review a {
  color: #007bff;
  text-decoration: none;
}

.product-info .installment {
  font-size: 16px;
  color: #6f42c1;
  margin-bottom: 20px;
}

.product-info .installment a {
  text-decoration: none;
}

.seller {
  background-color: #f8f9fa;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 10px;
  margin-bottom: 20px;
}

.seller-info {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.seller-info label {
  font-size: 14px;
  margin-left: 10px;
  color: #555;
}

.seller-info .rating {
  margin-left: auto;
  font-size: 14px;
  color: green;
}

.price {
  font-size: 20px;
  font-weight: bold;
  color: #222;
}

.shipping-time {
  font-size: 12px;
  color: #888;
  margin-top: 5px;
}

.add-to-cart {
  padding: 15px;
  font-size: 16px;
  color: #fff;
  background-color: #ffc107;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: bold;
}

.add-to-cart:hover {
  background-color: #ffa000;
}
</style>
