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
          {{ column.expanded ? "Daha Az Göster <" : "Tümünü Gör >" }}
        </button>
      </div>
    </div>

    <!-- Dil Seçenekleri -->
    <div class="language-options">
      <!-- Dil Seçenekleri -->
      <ul>
        <li
          v-for="(language, index) in languages"
          :key="index"
          :class="{ active: language === 'Türkçe' }"
        >
          {{ language }}
        </li>
      </ul>
      <!-- Sosyal Medya Logoları -->
      <div class="social-media-logos">
        <span>Bizi Takip Edin</span>
        <a
          v-for="(logo, index) in socialMediaLogos"
          :key="index"
          :href="logo.href"
          target="_blank"
        >
          <img :src="logo.src" :alt="logo.alt" />
        </a>
      </div>
    </div>

    <!-- Ortaklar ve Sponsorlar -->
    <div class="partners-container">
      <div class="partners-slider">
        <!-- Partner Kartları -->
        <div
          class="partners-list"
          :style="{
            transform: `translateX(-${currentIndex * (3 / visibleCount)}%)`,
          }"
        >
          <div
            class="partner"
            v-for="(partner, index) in visiblePartners"
            :key="index"
          >
            <img :src="partner.logo" :alt="partner.name" />
          </div>
        </div>
        <!-- Sol Ok -->
        <button
          class="arrow left"
          @click="prevSlide"
          :disabled="currentIndex === 0"
        >
          ‹
        </button>
        <!-- Sağ Ok -->
        <button
          class="arrow right"
          @click="nextSlide"
          :disabled="currentIndex + visibleCount >= partners.length"
        >
          ›
        </button>
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
      socialMediaLogos: [
        {
          href: "https://www.twitter.com",
          src: "https://img.icons8.com/?size=100&id=fJp7hepMryiw&format=png&color=ffffff",
        },
        {
          href: "https://www.facebook.com",
          src: "https://img.icons8.com/?size=100&id=98972&format=png&color=ffffff",
        },
        {
          href: "https://www.instagram.com",
          src: "https://img.icons8.com/?size=100&id=32320&format=png&color=ffffff",
        },
        {
          href: "https://www.youtube.com",
          src: "https://img.icons8.com/?size=100&id=85162&format=png&color=ffffff",
        },
        {
          href: "https://www.linkedin.com",
          src: "https://img.icons8.com/?size=100&id=98960&format=png&color=ffffff",
        },
      ],
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
      // Eğer genişletildiyse tüm linkleri göster, aksi halde ilk 10 linki göster.
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
  transition: transform 0.3s ease; /* Yumuşak kaydırma için geçiş ekleyin */
  width: calc(
    100% * 14 / 9
  ); /* Kaydırma işlemi için sabit bir genişlik belirleyin */
}

.partner {
  filter: brightness(0.8);
  cursor: pointer;
  flex: 0 0 calc(100% / 9);
  /* Her partner için genişlik */
  transition: transform 0.5s ease;
}
.partner:hover {
  filter: brightness(1.4); /* Parlaklığı artır */
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
  left: -60px;
  bottom: 10px;
}

.arrow.right {
  position: absolute;
  right: -40px;
}

.arrow:disabled {
  background: #ddd;

  color: #aaa;
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

.language-options {
  display: flex; /* İki bölümü yatayda hizalar */
  align-items: center; /* Dikeyde ortalar */
  justify-content: space-between; /* Dil seçenekleri solda, logolar sağda */
  background-color: #002f6c; /* Arka plan rengi */
  padding: 10px 20px; /* İçerik boşluğu */
  border-top: 1px solid #3d61ae; /* Üst çizgi */
  color: white; /* Yazı rengi */
}

.language-options ul {
  display: flex; /* Dil seçeneklerini yatay hizalar */
  gap: 15px; /* Diller arası boşluk */
  list-style: none; /* Liste işaretlerini kaldırır */
  margin: 0;
  padding: 0;
}

.language-options li {
  color: #777; /* Varsayılan renk */
  font-weight: normal;
  cursor: pointer;
  transition: color 0.3s ease, font-weight 0.3s ease, text-decoration 0.3s ease;
}

.language-options li:hover {
  color: #fff; /* Üzerine gelince beyaz */
  font-weight: bold; /* Kalın font */
  text-decoration: underline; /* Alt çizgi */
}

.language-options li.active {
  color: #fff; /* Aktif dil beyaz */
  font-weight: bold; /* Kalın font */
  text-decoration: underline; /* Alt çizgi */
}

.social-media-logos {
  display: flex; /* Sosyal medya logolarını yatay hizalar */
  gap: 15px; /* Logolar arası boşluk */
  align-items: center; /* Metin ve logoları hizalar */
}

.social-media-logos span {
  font-size: 14px;
  color: #ccc;
  margin-right: 10px;
}

.social-media-logos img {
  width: 24px;
  height: 24px;
  transition: transform 0.3s ease, filter 0.3s ease;
  cursor: pointer;
}

.social-media-logos img:hover {
  filter: brightness(0.75) sepia(100%) saturate(1000%) hue-rotate(0deg); /* Sarı renk */
  transform: scale(1.2); /* Büyütme efekti */
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
