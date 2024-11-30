<template>
  <div class="campaigns-container">
    <h2>Kampanyalar</h2>
    <div class="campaigns-grid">
      <!-- Kampanya Kartları -->
      <div class="campaign-card" v-for="(campaign, index) in campaigns" :key="index"
        :style="{ backgroundImage: `url(${campaign.background})` }">
        <div class="campaign-content">
          <h3>{{ campaign.title }}</h3>
          <p>{{ campaign.description }}</p>
          <span>{{ campaign.discount }}</span>
        </div>
        <div class="campaign-image">
          <img :src="campaign.image" :alt="campaign.title" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      campaigns: [
        {
          title: "Mutfak ürünlerinde Kasım fırsatları",
          description: "İlk alışverişe özel 250 TL indirim çeki",
          discount: "Peşin fiyatına 6 taksit",
          background: "https://via.placeholder.com/800x400?text=Mutfak",
          image: "https://via.placeholder.com/200x200?text=Mutfak+Ürünleri",
        },
        {
          title: "Ev ürünlerinde Kasım fırsatları",
          description: "İlk alışverişe özel 250 TL indirim çeki",
          discount: "Peşin fiyatına 6 taksit",
          background: "https://via.placeholder.com/800x400?text=Ev+Ürünleri",
          image: "https://via.placeholder.com/200x200?text=Ev+Ürünleri",
        },
        {
          title: "Oyun ürünlerinde Kasım fırsatları",
          description: "İlk alışverişe özel 250 TL indirim çeki",
          discount: "Peşin fiyatına 6 taksit",
          background: "https://via.placeholder.com/800x400?text=Oyun+Ürünleri",
          image: "https://via.placeholder.com/200x200?text=Oyun+Ürünleri",
        },
      ],
    };
  },
};
</script>

<style scoped>
.campaigns-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.campaigns-container h2 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.campaigns-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: space-between;
}

.campaign-card {
  flex: 1 1 calc(50% - 10px);
  /* İki kart yatayda */
  background-size: cover;
  background-position: center;
  border-radius: 10px;
  color: white;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  min-height: 200px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.campaign-card:nth-child(3) {
  flex: 1 1 100%;
  /* Üçüncü kart tam genişlik */
  min-height: 300px;
}

.campaign-content h3 {
  font-size: 20px;
  margin-bottom: 10px;
}

.campaign-content p {
  font-size: 16px;
  margin-bottom: 5px;
}

.campaign-content span {
  font-size: 14px;
  font-weight: bold;
  color: #ffc107;
}

.campaign-image {
  max-width: 150px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.campaign-image img {
  max-width: 100%;
  border-radius: 10px;
}
</style>
