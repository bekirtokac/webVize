<template>
  <div class="sign-in-container">
    <!-- Giriş Yap Butonu -->
    <div
      class="sign-in-button"
      :class="{ expanded: isExpanded }"
      @click="toggleExpand"
    >
      <i class="icon">👤</i>
      <span>Giriş Yap</span>
      <i class="arrow" v-if="!isExpanded">▼</i>
      <i class="arrow" v-else>▲</i>
    </div>

    <!-- Genişleyen Menü -->
    <div class="expanded-menu" v-if="isExpanded">
      <div class="left">
        <img src="https://via.placeholder.com/150" alt="Promo" />
      </div>
      <div class="right">
        <h3>Giriş</h3>
        <p>Size özel ödeme avantajları ve fırsatlardan yararlanmak için giriş yapın.</p>
        <button class="sign-in-action">Giriş Yap / Üye Ol</button>
        <a href="#" class="corporate-login">Kurumsal Yetkili Girişi</a>
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
  },
};
</script>

<style scoped>
/* Genel Container */
.sign-in-container {
  position: relative;
  width: 300px;
  margin: 20px;
}

/* Dar Buton */
.sign-in-button {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 15px;
  background-color: #f7f9fc;
  border: 1px solid #ddd;
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

.sign-in-button.expanded {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  border-color: #ccc;
}

.sign-in-button i.icon {
  margin-right: 10px;
  font-size: 20px;
  color: #333;
}

.sign-in-button span {
  flex: 1;
  text-align: left;
  font-size: 16px;
  color: #333;
}

.sign-in-button i.arrow {
  font-size: 12px;
  color: #666;
}

/* Genişleyen Menü */
.expanded-menu {
  display: flex;
  flex-direction: row;
  border: 1px solid #ddd;
  border-top: none;
  border-radius: 0 0 10px 10px;
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 15px;
}

.expanded-menu .left {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-right: 10px;
}

.expanded-menu .left img {
  width: 100px;
  border-radius: 5px;
}

.expanded-menu .right {
  flex: 2;
}

.expanded-menu .right h3 {
  font-size: 18px;
  margin-bottom: 10px;
}

.expanded-menu .right p {
  font-size: 14px;
  margin-bottom: 15px;
  color: #666;
}

.expanded-menu .right .sign-in-action {
  width: 100%;
  padding: 10px 15px;
  background-color: #ffc107;
  border: none;
  border-radius: 5px;
  font-size: 14px;
  font-weight: bold;
  color: #000;
  cursor: pointer;
}

.expanded-menu .right .corporate-login {
  display: block;
  margin-top: 10px;
  font-size: 12px;
  color: #007bff;
  text-decoration: none;
  text-align: right;
}

.expanded-menu .right .corporate-login:hover {
  text-decoration: underline;
}
</style>
