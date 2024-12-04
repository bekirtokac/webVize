<template>
  <div class="product-detail-container">
    <!-- Sol: Ürün Görseli -->
    <div class="image-and-button">
      <div class="zoom-container">
        <img :src="product.image" :alt="product.name" class="product-image" />
      </div>
      <button class="view-details-button"></button>
    </div>

    <!-- Sağ: Ürün Detayları -->
    <div class="product-info">
      <a>{{ product.brand }}</a>
      <div class="product-header">
        <div class="product-title">
          <h2>
            Pro Plan Medium Adult Somonlu Hassas Yetişkin Köpek Maması 14 Kg
          </h2>
        </div>
        <div class="favorite-icon">
          <span v-if="!product.isFavorite">♡</span>
        </div>
      </div>
      <p class="review">Henüz yorum yok <a href="#">Yorum Yaz</a></p>
      <div class="installment-button">
        <span class="installment-text">
          Peşin Fiyatına <strong>4 Taksit!</strong>
        </span>
        <span class="installment-arrow">></span>
      </div>
      <div class="shipping-card">
        <!-- Ücretsiz Kargo Etiketi -->
        <div class="shipping-tag">Ücretsiz Kargo</div>

        <!-- Fiyat -->
        <div class="price">3.098,90 TL</div>

        <!-- Satıcı Bilgileri -->
        <div class="seller-info">
          <div class="seller-name">
            <input type="radio" name="seller" checked />
            <span>KUZEY PAZARLAMA</span>
          </div>
          <div class="rating">10.0</div>
        </div>

        <!-- Kargo Süresi -->
        <div class="shipping-time">3 iş gününde kargoda</div>
      </div>

      <button class="add-to-cart">Sepete Ekle</button>
      <div class="icon-container">
        <div class="icon" tabindex="0">
          <div class="icon-circle">
            <span class="material-icons">local_shipping</span>
            <!-- Google ikonu -->
          </div>
          <span>Ücretsiz Kargo</span>
        </div>
        <div class="icon" tabindex="0">
          <div class="icon-circle">
            <span class="material-icons">gpp_maybe</span>
            <!-- Google ikonu -->
          </div>
          <span>Turkcell Pasaj Garantisi</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        image:
          "https://ffo3gv1cf3ir.merlincdn.net//SiteAssets/pasaj/crop/cg/00FND9/1-1675797005058/1-1675797005058_600x450.png?1731801459000", // Örnek ürün görseli
        brand: "Pro Plan",

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
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");

.image-and-button {
  display: flex;
  flex-direction: column; /* Dikey hizalama */
  align-items: center; /* Ortalamak için */
  gap: 40px; /* Görsel ile buton arasındaki boşluk */
  width: 300px; /* Görsel genişliğine eşit */
  margin: 0 auto; /* Ortada hizalama */
}

.zoom-container {
  width: 100%;
  height: 400px;
  overflow: hidden;
  position: relative;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.zoom-container:hover .product-image {
  transform: scale(1.8);
  cursor: zoom-in;
}

.view-details-button {
  font-size: 16px;
  color: #fff;
  background-color: #2855ac;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: bold;
  width: 1.125rem; /* Genişlik ayarlandı */
  height: 0.3125rem; /* Yükseklik ayarlandı */
}

.icon-circle .material-icons {
  font-size: 30px; /* İkon boyutunu büyütmek için */
  color: #666; /* İkon rengi */
  transition: color 0.3s;
}

.icon:hover .material-icons,
.icon:focus .material-icons {
  color: white; /* Hover veya focus sırasında ikon rengi */
}

.icon-container {
  font-family: "Poppins", sans-serif;
  display: flex;
  gap: 20px;
  justify-content: center;
  align-items: center;
  margin-right: 600px;
  margin-top: 30px;
}

.icon {
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
  text-align: center;
  transition: color 0.3s, transform 0.3s;
}

.icon-circle {
  width: 60px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f2f2f2;
  border-radius: 50%;
  transition: background-color 0.3s, transform 0.3s;
}

.icon i {
  font-size: 24px;
  color: #666;
  transition: color 0.3s;
}

.icon span {
  margin-top: 8px;
  font-size: 14px;
  color: #666;
  transition: color 0.3s;
}

.icon:hover .icon-circle,
.icon:focus .icon-circle {
  background: linear-gradient(135deg, #ffcc00, #ff9900);
  transform: scale(1.1);
}

.icon:hover i,
.icon:focus i {
  color: white;
}

.icon:hover span,
.icon:focus span {
  color: #ff9900;
  font-weight: bold;
}

.product-detail-container {
  display: flex;
  gap: 20px;
  padding: 20px;
  background-color: #fff;
  width: 1200px;
  margin: auto;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
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
  margin-left: 100px;
}

.product-info a {
  font-family: "Poppins", sans-serif;
  font-size: 18px;
  color: #2855ac;
  margin-bottom: -20px;
}

.product-header {
  font-family: "Poppins", sans-serif;
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* Başlık ve kalp simgesini sağa ve sola hizalar */
  padding: 10px 0;
}

.product-title h2 {
  font-size: 38px;
  color: rgb(0, 0, 0);

  margin: 0;
  font-weight: 600;
}

.favorite-icon {
  font-size: 70px;
  cursor: pointer;
  color: #333;
  margin-bottom: 60px;
  /* Siyahımsı renk */
}

.favorite-icon:hover {
  color: #ffcc00;
  /* Kalbe tıklanabilirlik için hover rengi kırmızı */
}

.product-info .review {
  font-family: "Poppins", sans-serif;
  font-size: 14px;
  color: #888;
  margin-bottom: 10px;
}

.product-info .review a {
  color: #2855ac;
  text-decoration: none;
}

.shipping-card {
  border: 2px solid #4a90e2;
  /* Mavi kenar */
  border-radius: 10px;
  padding: 20px;
  background: #f5f9ff;
  /* Açık mavi arka plan */
  max-width: 600px;
  position: relative;
  font-family: Arial, sans-serif;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 10px;
  cursor: pointer;
  margin-top: 20px;
  height: 120px;
}

.shipping-tag {
  position: absolute;
  top: 0px;
  left: 0px;
  background: #2f5bb7;
  /* Mavi arka plan */
  color: white;
  padding: 5px 10px;
  font-size: 14px;
  border-radius: 5px;
}

.price {
  font-size: 24px;
  color: #2f5bb7;
  /* Mavi renk */
  font-weight: bold;
  align-self: flex-start;
  /* Sol köşeye hizalar */
}

.seller-info {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.seller-name {
  font-family: "Poppins", sans-serif;
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 18px;
  color: #2f5bb7;
  /* Mavi renk */
}

.seller-name input[type="radio"] {
  accent-color: #ffcc00;
  /* Sarı renkli radio butonu */
}

.rating {
  background: #28a745;
  /* Yeşil arka plan */
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 16px;
  font-weight: bold;
  align-self: flex-start;
  /* Sol tarafta yer almasını sağlar */
}

.shipping-time {
  font-size: 14px;
  color: #888;
  /* Gri renk */
  align-self: flex-start;
  margin-left: 460px;
  /* Sol tarafa hizalar */
}

.price-info {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 10px;
}

.price {
  font-size: 24px;
  color: #2f5bb7;
  /* Mavi renk */
  font-weight: bold;
  margin-left: 470px;
}

.add-to-cart {
  font-family: "Poppins", sans-serif;
  padding: 15px;
  font-size: 16px;
  color: #253342;
  background-color: #ffc900;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: bold;
  margin-top: 50px;
  width: 650px;
}

.add-to-cart:hover {
  filter: brightness(1.1);
}

.installment-button {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  border: 2px solid #9b59b6;
  /* Mor renk */
  border-radius: 12px;
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: normal;
  color: #4b0082;
  /* Mor yazı rengi */
  cursor: pointer;
  width: 345px;
  margin-top: 10px;
}

.installment-text {
  display: flex;
  align-items: center;
}

.installment-arrow {
  margin-left: 10px;
  font-weight: bold;
  font-size: 18px;
  color: #4b0082;
  /* Ok rengi */
}
</style>
