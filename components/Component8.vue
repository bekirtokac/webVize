<template>
  <div class="campaigns-container">
    <h2 class="header">Kampanyalar</h2>
    <div class="campaigns-layout">
      <!-- Sol Bölüm: Mutfak ve Ev Ürünleri -->
      <div class="left-column">
        <div class="campaign-card" v-for="(campaign, index) in leftColumnCampaigns" :key="index">
          <img :src="campaign.background" :alt="campaign.title" class="campaign-image" />
          <div class="campaign-content">
            <h3>{{ campaign.title }}</h3>
            <p>{{ campaign.description }}</p>
            <span>{{ campaign.discount }}</span>
          </div>
        </div>
      </div>

      <!-- Sağ Bölüm: Oyun Ürünleri -->
      <div class="right-column">
        <img :src="rightColumnCampaign.background" :alt="rightColumnCampaign.title" class="campaign-image" />
        <div class="campaign-content">
          <h3>{{ rightColumnCampaign.title }}</h3>
          <p>{{ rightColumnCampaign.description }}</p>
          <span>{{ rightColumnCampaign.discount }}</span>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      leftColumnCampaigns: [
        {
          background: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/kampanya/yatay/36aytaksit-kampanyalar-yatay-fwebx.jpg?1731801459000",
        },
        {
          background: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/kampanya/yatay/r1-pac-jbl--yatay-web.jpg?1731801459000",
        },
      ],
      rightColumnCampaign: {

        background: "https://ffo3gv1cf3ir.merlincdn.net/SiteAssets/Cihaz/pasaj/kampanya/dikey/hk45k-kampanyalar-dikey.jpg?1731801459000",
      },
    };
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");

.header {
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  font-size: 50px;
  margin: 0;
}

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

.campaigns-layout {
  display: flex;
  gap: 20px;
}

/* Sol Bölüm */
.left-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.left-column .campaign-card {
  width: 100%;
  height: 280px;
  /* Sabit yükseklik */
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
}

.left-column .campaign-image {
  width: 780px;
  height: 280px;
  object-fit: cover;
}

/* Sağ Bölüm */
.right-column {
  flex: 2;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.right-column .campaign-card {
  width: 100%;
  height: 280px;
  /* Sabit yükseklik */
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  position: relative;
}

.right-column .campaign-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* İçerik */
.campaign-content {
  position: absolute;
  bottom: 20px;
  left: 20px;
  color: white;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.6);
}

.campaign-content h3 {
  font-size: 18px;
  margin-bottom: 10px;
}

.campaign-content p {
  font-size: 14px;
  margin-bottom: 10px;
}

.campaign-content span {
  font-size: 14px;
  font-weight: bold;
  color: #ffc107;
}
</style>
