<template>
  <div id="app">
    <Header :basket="basket" :removeBasketList="removeBasketList" />
    <MainSection :products="products" :basket="basket" />
    <Footer />
  </div>
</template>

<script>
import MainSection from "./components/mainSection/MainSection.vue";
import Header from "./components/header/Header.vue";
import Footer from "./components/footer/Footer.vue";

import productsList from "./assets/product-list/products.json";

export default {
  name: "App",
  components: {
    MainSection,
    Header,
    Footer
  },
  data() {
    return {
      basket: [],
      products: [...productsList]
    };
  },
  methods: {
    removeBasketList() {
      this.basket.forEach(product => (product.counter = 0));
      return (this.basket = []);
    }
  }
};
</script>
