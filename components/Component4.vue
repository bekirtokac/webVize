<template>
  <div class="sign-in-container" @click="closeExpand">
    <!-- Giriş Yap Butonu -->
    <div
      class="sign-in-button"
      :class="{ expanded: isExpanded }"
      @click.stop="toggleExpand"
    >
      <span style="font-size: 30px; padding-right: 5px; padding-left: 10%;" class="material-symbols-outlined">account_circle</span>
      <span style="padding-left: 5px; padding-right: 5px;">Giriş Yap</span>
      <i class="arrow" v-if="!isExpanded" style="margin-left: 5px;">▼</i>
      <i class="arrow" v-else style="margin-left: 5px;">▼</i>
    </div>

    <!-- Genişleyen Menü -->
    <div class="expanded-menu" v-if="isExpanded">
      <div class="left">
        <img src="https://ffo3gv1cf3ir.merlincdn.net/pasaj_static_lib/passage-assets/common/images/content/login-image.png" alt="Promo" />
        <p class="welcome-message">
          <span style="font-size: 24px; font-weight:600;">Turkcell Pasaj’ın fırsatlarla dolu dünyasına hoş geldiniz!</span><br />
          <span style="font-size: 14px;color: rgb(37, 51, 66);">Turkcell Pasaj’da fırsatlar bitmez! İhtiyacınız olan bir çok ürüne, güvenli ve esnek ödeme seçenekleri ile hem de kredi kartı limitinize takılmadan sahip olabilirsiniz. Favorilediğiniz ürünler için bilgilendirmelerden, siparişlerinizle ilgili tüm işlemlere ve daha da fazlasına kolaylıkla erişim sağlayabilirsiniz.</span>
        </p>
      </div>
      <div class="right">
        <h3>Giriş</h3>
        <p style="font-weight: 400;">Size özel ödeme avantajları ve size özel tekliflerden faydalanmak için Giriş Yap/Üye Ol seçeneği ile devam edebilirsiniz.</p>
        <button style="font-weight: 400;font-size: 24px;" class="sign-in-action">Giriş Yap / Üye Ol</button>
        <div class="o-p-header__dropdown__login__break o-p-header__dropdown__login__break--empty" style="width: 470px; height: 1px; background-color: rgb(222, 227, 237); margin-top: 20px;"></div>
        <a href="#" style="font-weight: 600;" class="corporate-login">Kurumsal Yetkili Girişi</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isExpanded: false, // Menü genişleme durumu
    };
  },
  methods: {
    toggleExpand() {
      this.isExpanded = !this.isExpanded;
    },
    closeExpand(event) {
      if (this.isExpanded && !this.$el.contains(event.target)) {
        this.isExpanded = false;
      }
    },
  },
  mounted() {
    document.addEventListener("click", this.closeExpand);
  },
  beforeDestroy() {
    document.removeEventListener("click", this.closeExpand);
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200&icon_names=account_circle');
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

/* Genel Container */
.sign-in-container {
  position: relative;
  width: 90%;
  margin: 20px;
  font-family: 'Poppins', serif;
}

/* Dar Buton */
.sign-in-button {
  margin-left: 75%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 175px;
  height: 60px;
  padding: 10px 5px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  font-family: 'Poppins', serif;
}

.sign-in-button.expanded {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  border-color: #ccc;
}

.sign-in-button span {
  text-align: left;
  font-size: 16px;
  color: #333;  
  margin-left: 0;
}

.sign-in-button i.arrow {
  font-size: 12px;
  color: #666;
  margin-left: 3px;
}

/* Genişleyen Menü */
.expanded-menu {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  display: flex;
  flex-direction: row;
  border: 1px solid rgb(246, 245, 248);
  border-top: none;
  border-radius: 0 0 10px 10px;
  background-color: rgb(246, 245, 248);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  justify-content: center;
  align-items: center;
  font-family: 'Poppins', serif;
  gap: 20%;
}

.expanded-menu .left {
  padding-left: 10%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  
}

.expanded-menu .left img {
  margin-left: 25%;
  width: 350px;
  height: 200px;
  border-radius: 5px;
  object-fit: cover;
}

.expanded-menu .left .welcome-message {
  margin-left: 25%;
  width: 420px;
  text-align: left;
}

/*komple sağ taraf */
.expanded-menu .right {
  padding-right: 5%;
  text-align: left;
  font-family: 'Poppins', serif;
  margin-bottom: 12%;
}
/*giris yazısı */
.expanded-menu .right h3 {
  font-size: 32px;
  margin-bottom: -5px;
  color: #333;
}

/*size özel yazısı */
.expanded-menu .right p {
  font-weight: 600;
  font-style: normal;
  font-size: 14px;
  margin-bottom: 20px;
  padding-right: 30%;
  color: #666;
}

.expanded-menu .right .sign-in-action {
  width: 70%;
  padding: 2%;
  background-color: #ffc107;
  border: none;
  border-radius: 200px;
  font-size: 20px;
  font-weight: bold;
  color: rgb(37, 51, 66);
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.expanded-menu .right .sign-in-action:hover {
  background-color: #e0a800;
}

/*kurumsal yetkili giriş */
.expanded-menu .right .corporate-login {
  padding-right: 30%;
  display: block;
  margin-top: 15px;
  font-size: 13px;
  color: #ffc107;
  text-decoration: none;
  text-align: right;
}

.expanded-menu .right .corporate-login:hover {
  text-decoration: underline;
}

.material-symbols-outlined {
  font-variation-settings:
  'FILL' 0,
  'wght' 400,
  'GRAD' 0,
  'opsz' 24;
  margin-right: 0;
}
</style>
