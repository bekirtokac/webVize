<template>
    <MainLayout>
      <div>
        <Navbar />
        <Component1 />
        <Component2 />
      </div>
    </MainLayout>
  </template>
  
  <script>
  import MainLayout from '~/layouts/MainLayout.vue';
  import Navbar from '~/components/Navbar.vue';
  import Component1 from '~/components/Component1.vue';
  import Component2 from '~/components/Component2.vue';
  
  export default {
    components: {
      MainLayout,
      Navbar,
      Component1,
      Component2,
    },
  };
  </script>
  