<template>
  <footer class="footer-container">
    <!-- Üst Bölüm: Ana Linkler -->
    <div class="main-links">
      <div
        v-for="(column, index) in mainLinks"
        :key="index"
        class="link-column"
      >
        <h4>{{ column.title }}</h4>
        <ul>
          <li v-for="(link, idx) in visibleLinks(column)" :key="idx">
            {{ link }}
          </li>
        </ul>
        <button
          v-if="column.showMore"
          @click="toggleShowMore(index)"
          class="show-more"
        >
          {{ column.expanded ? "Daha Az Göster<" : "Tümünü Gör >" }}
        </button>
      </div>
    </div>

    <!-- Dil Seçenekleri -->
    <div class="language-options">
      <ul>
        <li
          v-for="(language, index) in languages"
          :key="index"
          :class="{ active: language === 'Türkçe' }"
        >
          {{ language }}
        </li>
      </ul>
    </div>

    <!-- Ortaklar ve Sponsorlar -->
    <div class="partners-container">
      <div class="partners-slider">
        <!-- Sol Ok -->
        <button class="arrow left" @click="prevSlide">‹</button>
        <!-- Partner Kartları -->
        <div class="partners-list">
          <div
            class="partner"
            v-for="(partner, index) in partners"
            :key="index"
          >
            <img :src="partner.logo" :alt="partner.name" />
          </div>
        </div>
        <!-- Sağ Ok -->
        <button class="arrow right" @click="nextSlide">›</button>
      </div>
    </div>

    <!-- Alt Bölüm: Yasal Linkler ve Logo -->
    <div class="bottom-info">
      <div class="legal-links">
        <a href="#">Gizlilik ve Güvenlik</a>
        <a href="#">Tarife Karşılaştırma</a>
      </div>
      <div class="logos">
        <img
          v-for="(logo, index) in bottomLogos"
          :key="index"
          :src="logo.src"
          :alt="logo.alt"
        />
        <span>© 2024 Turkcell</span>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      mainLinks: [
        {
          title: "Hakkımızda",
          links: [
            "Genel Bakış",
            "Haberler & Duyurular",
            "Kurumsal İletişim ve Sürdürülebilirlik",
            "Kariyer",
            "Gizlilik ve Güvenlik",
            "İletişim",
            "Pasaj’da Satıcı Ol",
            "Pasaj Blog",
            "Pasaj Gaming",
            "Telefon Sat",
          ],
          showMore: false,
          expanded: false,
        },
        {
          title: "Popüler Kategoriler",
          links: [
            "Android Telefonlar",
            "iPhone Telefonlar",
            "İkinci El / Yenilenmiş Telefonlar",
            "Akıllı Saatler",
            "Bluetooth Kulaklıklar",
            "Telefon Kılıfları",
            "Tabletler",
            "Laptop",
            "Oyun Bilgisayarları",
            "Modemler",
            "Dikey Süpürgeler",
            "Robot Süpürgeler",
            "Kahve Makineleri",
            "Klimalar",
            "Televizyonlar",
            "Oyun Konsolları",
            "Scooter & Bisikletler",
          ],
          showMore: true,
          expanded: false,
        },
        {
          title: "Yardım",
          links: [
            "Yardım Merkezi",
            "İşlem Rehberi",
            "Sipariş Sorgulama",
            "Nasıl İade Edebilirim?",
          ],
          showMore: false,
          expanded: false,
        },
        {
          title: "Markalar",
          links: [
            "Apple",
            "Samsung",
            "Dyson",
            "Anker",
            "Arzum",
            "Beko",
            "Bosch",
            "Braun",
            "Casper",
            "Delonghi",
            "Huawei",
            "JBL",
            "Karaca",
            "Karcher",
            "Lego",
            "Lenovo",
            "Omix",
            "Philips",
            "Realme",
            "Xiaomi",
          ],
          showMore: true,
          expanded: false,
        },
        {
          title: "Özel Günler & Kampanyalar",
          links: [
            "Ramazan Kampanyası",
            "Ramazan Teklifleri",
            "Düğün ve Çeyiz Paketleri",
            "Telefon Sat",
            "Eskiyi Getir Yeniyi Al",
            "Teknolojik Cihaz Desteği",
            "Vergisiz Telefonlar",
            "Vergisiz Bilgisayarlar",
            "Fırsatlar Pasajı",
            "Pasaj Günleri",
            "Sarı Günler",
            "Uykusuz Kaçanlar Kulübü",
            "Sevgililer Günü Hediyeleri",
            "Anneler Günü Hediyeleri",
            "Babalar Günü",
            "Okula Dönüş Kampanyası",
            "Şehre Dönüş Kampanyası",
            "Karne Hediyeleri",
            "Yılbaşı Hediyeleri",
            "Kurban Bayramı Kampanyası",
            "Resmi Tatil Günleri",
          ],
          showMore: true,
          expanded: false,
        },
        {
          title: "Popüler Ürünler",
          links: [
            "iPhone 15",
            "iPhone 16",
            "iPhone 15 Plus",
            "iPhone 15 Pro",
            "iPhone 15 Pro Max",
            "iPhone 14",
            "iPhone 14 Plus",
            "iPhone 14 Pro",
            "iPhone 14 Pro Max",
            "iPhone 13",
            "iPhone 13 Mini",
            "iPhone 12",
            "iPhone 11",
            "Dyson V15 Detect",
            "Xiaomi Redmi Note 13",
            "Samsung Galaxy S24 Ultra",
            "Samsung Galaxy A04",
            "Samsung Galaxy A25",
            "PS5/Playstation 5",
            "Dyson Airstrait",
            "TV+ Ready",
          ],
          showMore: true,
          expanded: false,
        },
      ],
      languages: ["Türkçe", "English", "العربية", "русский"],
      partners: [
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/fizy-logo.png?17735349480651",
          name: "Partner 1",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/sol-yeni-logo.png?1731801459000",
          name: "Partner 2",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/platinum-logo.png?1731801459000",
          name: "Partner 3",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/bip-logo.png?1731801459000",
          name: "Partner 4",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/tv-plus-logo-yeni.png?1731801459000",
          name: "Partner 5",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/LifeBox-Logo.png?1731801459000",
          name: "Partner 6",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/paycell_logo2.png?1731801459000",
          name: "Partner 7",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/gnc-logo.png?1731801459000",
          name: "Partner 8",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/logo_gaming.png?1731801459000",
          name: "Partner 9",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/suit-logo2.png?1731801459000",
          name: "Partner 10",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/Global-Bilgi-Logo.png?1731801459000",
          name: "Partner 11",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/wiyo-v2.png?1731801459000",
          name: "Partner 12",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/Gelecegi-YazanKadinlar-Logo.png?1731801459000",
          name: "Partner 13",
        },
        {
          logo: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Kategori/menu/Turkcell-Bulut.png?1731801459000",
          name: "Partner 14",
        },
      ],
      currentIndex: 0,
      visibleCount: 9,

      bottomLogos: [
        {
          src: "https://ffo3gv1cf3ir.merlincdn.net/pasaj_static_lib/assetsv2/common/images/icons/guven-damgasi-icon.png?1731801459000",
          alt: "TR GO Logo",
        },
        {
          src: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Genel/ana-sayfa/etbis-qr-code.png?1731801459000",
          alt: "QR Code",
        },
      ],
    };
  },

  computed: {
    visiblePartners() {
      return this.partners.slice(
        this.currentIndex,
        this.currentIndex + this.visibleCount
      );
    },
  },

  methods: {
    nextSlide() {
      if (this.currentIndex + this.visibleCount < this.partners.length) {
        this.currentIndex++;
      }
    },
    prevSlide() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
    toggleShowMore(index) {
      this.mainLinks[index].expanded = !this.mainLinks[index].expanded;
    },
    visibleLinks(column) {
      return column.expanded ? column.links : column.links.slice(0, 10);
    },
  },
};
</script>




<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
.partners-container {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.partners-slider {
  display: flex;
  align-items: center;
  position: relative;
}

.partners-list {
  display: flex;
  overflow: hidden;
  width: 100%;
}

.partner {
  flex: 0 0 calc(100% / 9);
  /* Her partner için genişlik */
  transition: transform 0.5s ease;
}

.partner img {
  max-width: 100%;
  height: auto;
}

.arrow {
  background: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  font-size: 20px;
  z-index: 1;
  transform: translateY(-50%);
}

.arrow:hover {
  background: #007bff;
  color: white;
}

.arrow.left {
  position: absolute;
  left: -20px;
}

.arrow.right {
  position: absolute;
  right: -20px;
}
.footer-container {
  font-family: "Poppins", sans-serif;
  background-color: #002f6c;
  color: white;
  padding: 20px;
  font-size: 14px;
}

.main-links {
  font-family: "Poppins", sans-serif;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  gap: 20px;
  flex-wrap: wrap;
}

.link-column {
  flex: 1;
  min-width: 180px;
}

.link-column h4 {
  font-weight: bold;
  margin-bottom: 10px;
}
.link-column h4:hover {
  color: #ffcc00;
}

.link-column ul {
  list-style: none;
  padding: 0;
}

.link-column li {
  margin-bottom: 5px;
}
.link-column li:hover {
  color: #ffcc00;
}

.show-more {
  text-decoration-line: underline;
  font-family: "Poppins", sans-serif;
  background: none;
  border: none;
  color: #fff;
  cursor: pointer;
  margin-top: 10px;
}

.language-options ul {
  border-top: 1px solid #3d61ae;
  list-style-type: none; /* Madde işaretlerini kaldır */
  padding: 0;
  margin-top: 30px;
  display: flex;
  gap: 15px; /* Diller arası boşluk */
}

.language-options li {
  margin-top: 30px;
  color: #777; /* Normalde soluk gri */
  font-weight: normal; /* Normal kalınlık */
  transition: color 0.3s ease-in-out, font-weight 0.3s ease-in-out,
    text-decoration 0.3s ease-in-out; /* Geçiş animasyonu */
  cursor: pointer; /* İmleç geldiğinde el işareti */
}

.language-options li:hover {
  color: #fff; /* İmleç gelince beyaz */
  font-weight: bold; /* İmleç gelince kalın */
  text-decoration: underline; /* İmleç gelince alt çizgi */
}

.language-options li.active {
  color: #fff; /* Türkçe dili beyaz renk */
  font-weight: bold; /* Kalın font */
  text-decoration: underline; /* Alt çizgi */
}

.bottom-info {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
  border-top: 1px solid #3d61ae;
  padding-top: 20px;
}

.legal-links a {
  margin-right: 20px;
  color: #ccc;
}
.legal-links a:hover {
  color: #ffcc00;
}

.logos {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logos img {
  max-width: 40px;
}
</style>
