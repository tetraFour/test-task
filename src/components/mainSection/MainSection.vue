<template>
  <main>
    <div class="container">
      <Filters />
      <OnSale
        :products="products"
        :setPriceConvert="setPriceConvert"
        :addToBasket="addToBasket"
      />
      <NewListings
        :products="products"
        :setPriceConvert="setPriceConvert"
        :addToBasket="addToBasket"
      />
      <News />
    </div>
  </main>
</template>

<script>
import Filters from "./Filters";
import OnSale from "./OnSale";
import NewListings from "./NewListings";
import News from "./News";

export default {
  name: "MainSection",
  props: ["products", "basket"],
  components: { Filters, OnSale, NewListings, News },

  methods: {
    setPriceConvert(product) {
      return `${product}.00$`;
    },
    addToBasket(event, product) {
      if (product.counter !== 0) {
        event.preventDefault();
      } else {
        product.counter += 1;
        return this.basket.push(product);
      }
    }
  }
};
</script>
