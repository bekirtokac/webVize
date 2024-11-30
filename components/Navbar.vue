<template>
  <nav>
    <ul>
      <li v-for="i in 10" :key="i">
        <button @click="setActiveComponent(`Component${i}`)">
          Component {{ i }}
        </button>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    setActiveComponent: {
      type: Function,
      required: true,
    },
  },
};
</script>


<style scoped>
nav {
  background: #f4f4f4;
  padding: 10px;
  display: flex;
  flex-direction: column;
}

button {
  margin: 5px 0;
  padding: 10px;
  border: 1px solid #ddd;
  background: #fff;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background: #e0e0e0;
}
</style>
