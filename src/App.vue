<template>
  <div>
    <navbar></navbar>
    <products></products>
  </div>
</template>

<script>
import products from "./components/products.vue";
import navbar from "./components/navbar.vue";

export default {
  name: "App",
  components: {
    navbar,
    products,
  },
};
</script>

