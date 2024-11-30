<template>
  <footer class="footer" style="height: 1000px;">
    <div class="footer-top">
      <!-- Footer Bölümleri -->
      <div class="footer-column" v-for="(section, index) in footerSections" :key="index">
        <h4>{{ section.title }}</h4>
        <ul>
          <li v-for="(item, idx) in section.items" :key="idx">
            <a href="#">{{ item }}</a>
          </li>
        </ul>
        <a href="#" class="view-all">Tümünü Gör</a>
      </div>
    </div>

    <div class="footer-middle" style="">
      <!-- Dil Seçimi -->
      <div class="language-selection">
        <a href="#">Türkçe</a>
        <a href="#">English</a>
        <a href="#">عربي</a>
        <a href="#">русский</a>
      </div>

      <!-- Markalar -->
      <div class="brands">
        <img src="https://via.placeholder.com/50" alt="Marka 1" />
        <img src="https://via.placeholder.com/50" alt="Marka 2" />
        <img src="https://via.placeholder.com/50" alt="Marka 3" />
        <img src="https://via.placeholder.com/50" alt="Marka 4" />
        <img src="https://via.placeholder.com/50" alt="Marka 5" />
      </div>
    </div>

    <div class="footer-bottom">
      <!-- Alt Bilgiler -->
      <div class="bottom-links">
        <a href="#">Gizlilik ve Güvenlik</a>
        <a href="#">Tarife Karşılaştırma</a>
      </div>

      <!-- Sosyal Medya -->
      <div class="social-media">
        <span>Bizi Takip Edin</span>
        <a href="#"><i class="icon-facebook"></i></a>
        <a href="#"><i class="icon-twitter"></i></a>
        <a href="#"><i class="icon-instagram"></i></a>
        <a href="#"><i class="icon-youtube"></i></a>
        <a href="#"><i class="icon-linkedin"></i></a>
      </div>

      <div class="copyright">
        © 2024 Turkcell
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      footerSections: [
        {
          title: "Hakkımızda",
          items: [
            "Genel Bakış",
            "Haberler & Duyurular",
            "Kariyer",
            "Gizlilik ve Güvenlik",
            "İletişim",
            "Pasaj Blog",
          ],
        },
        {
          title: "Popüler Kategoriler",
          items: [
            "Android Telefonlar",
            "iPhone Telefonlar",
            "Tabletler",
            "Laptop",
            "Akıllı Saatler",
          ],
        },
        {
          title: "Yardım",
          items: [
            "Yardım Merkezi",
            "İşlem Rehberi",
            "Sipariş Sorgulama",
            "Nasıl İade Edebilirim?",
          ],
        },
        {
          title: "Markalar",
          items: [
            "Apple",
            "Samsung",
            "Dyson",
            "Anker",
            "Braun",
            "Casper",
          ],
        },
        {
          title: "Özel Günler & Kampanyalar",
          items: [
            "Ramazan Kampanyası",
            "Telefon Sat",
            "Fırsatlar Pasajı",
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.footer {
  background-color: #002147;
  color: white;
  padding: 40px 20px;
  font-family: Arial, sans-serif;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}

.footer-column {
  flex: 1;
}

.footer-column h4 {
  font-size: 16px;
  margin-bottom: 10px;
  color: #ddd;
}

.footer-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-column ul li {
  margin-bottom: 5px;
}

.footer-column ul li a {
  text-decoration: none;
  color: #bbb;
  font-size: 14px;
}

.footer-column ul li a:hover {
  color: #ffcc00;
}

.view-all {
  display: block;
  margin-top: 10px;
  color: #007bff;
  text-decoration: none;
  font-size: 14px;
}

.view-all:hover {
  text-decoration: underline;
}

.footer-middle {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
  border-top: 1px solid #555;
  border-bottom: 1px solid #555;
}

.language-selection a {
  margin-right: 15px;
  color: #bbb;
  text-decoration: none;
  font-size: 14px;
}

.language-selection a:hover {
  color: #ffcc00;
}

.brands img {
  margin: 0 10px;
  width: 50px;
  height: auto;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}

.bottom-links a {
  margin-right: 15px;
  color: #bbb;
  text-decoration: none;
  font-size: 14px;
}

.bottom-links a:hover {
  color: #ffcc00;
}

.social-media {
  display: flex;
  align-items: center;
}

.social-media span {
  margin-right: 10px;
  font-size: 14px;
}

.social-media a {
  margin: 0 5px;
  color: #bbb;
  text-decoration: none;
  font-size: 20px;
}

.social-media a:hover {
  color: #ffcc00;
}

.copyright {
  font-size: 12px;
  color: #888;
}
</style>
