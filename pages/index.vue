<template>
  <div class="container">
    <!-- Sol tarafta Navbar -->
    <div class="navbar">
      <Navbar :setActiveComponent="setActiveComponent" />
    </div>

    <!-- Sağ tarafta Componentler -->
    <div class="content">
      <Component1 v-show="activeComponent === 'Component1'" />
      <Component2 v-show="activeComponent === 'Component2'" />
      <Component3 v-show="activeComponent === 'Component3'" />
      <Component4 v-show="activeComponent === 'Component4'" />
      <Component5 v-show="activeComponent === 'Component5'" />
      <Component6 v-show="activeComponent === 'Component6'" />
      <Component7 v-show="activeComponent === 'Component7'" />
      <Component8 v-show="activeComponent === 'Component8'" />
      <Component9 v-show="activeComponent === 'Component9'" />
      <Component10 v-show="activeComponent === 'Component10'" />
    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import Component1 from '~/components/Component1.vue';
import Component2 from '@/components/Component2.vue';
import Component3 from '@/components/Component3.vue';
import Component4 from '~/components/Component4.vue';
import Component5 from '~/components/Component5.vue';
import Component6 from '~/components/Component6.vue';
import Component7 from '~/components/Component7.vue';
import Component8 from '~/components/Component8.vue';
import Component9 from '~/components/Component9.vue';
import Component10 from '~/components/Component10.vue';


export default {
  components: {
    Navbar,
    Component1,
    Component2,
    Component3,
    Component4,
    Component5,
    Component6,
    Component7,
    Component8,
    Component9,
    Component10,
  },
  data() {
    return {
      activeComponent: 'Component1', // Başlangıç componenti
    };
  },
  methods: {
    setActiveComponent(component) {
      this.activeComponent = component; // Aktif componenti değiştir
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  /* Navbar ve content yan yana */
  height: 100vh;
  /* Tam ekran yüksekliği */
}

.navbar {
  width: 200px;
  /* Navbar genişliği */
  background-color: #f4f4f4;
  /* Açık gri arka plan */
  padding: 10px;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
  /* Hafif gölge */
}

.content {
  flex: 1;
  /* Geri kalan alanı kaplar */
  padding: 20px;
  background-color: #fff;
  /* Beyaz arka plan */
}
</style>
