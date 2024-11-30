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
  display: flex;
  flex-direction: column;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 10px;
}

button {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  background-color: #fff;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background-color: #007bff;
  color: white;
}
</style>
