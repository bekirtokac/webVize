<template>
  <div class="layout">
    <!-- Sol Navigation Bar -->
    <aside class="nav-bar">
      <button
        v-for="(component, index) in components"
        :key="index"
        @click="currentComponent = index"
      >
        {{ `Component ${index + 1}` }}
      </button>
    </aside>

    <!-- Sağ Main Bar -->
    <main class="main-bar">
      <component
        v-for="(component, index) in components"
        :is="component"
        :key="index"
        v-show="currentComponent === index"
      />
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentComponent: 0, // Başlangıçta birinci bileşen görünecek
      components: [
        "Component1",
        "Component2",
        "Component3",
        "Component4",
        "Component5",
        "Component6",
        "Component7",
        "Component8",
        "Component9",
        "Component10",
      ],
    };
  },
};
</script>

<style scoped>
.layout {
  display: flex;
  height: 100vh;
}

.nav-bar {
  width: 200px;
  background-color: #f4f4f4;
  padding: 10px;
}

.nav-bar button {
  width: 100%;
  margin-bottom: 5px;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}

.nav-bar button:hover {
  background-color: #0056b3;
}

.main-bar {
  flex: 1;
  padding: 20px;
  background-color: #fff;
  overflow-y: auto;
}
</style>
