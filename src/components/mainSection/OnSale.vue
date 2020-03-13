<template>
  <section class="on-sale">
    <h2>On sale</h2>
    <div class="custom-scrollbar">
      <ul>
        <li v-for="product in products" :key="product.id" class="corner-dots">
          <div class="product-card-wrapper the-best">
            <h4 v-html="product.name"></h4>
            <div class="image-wrapper">
              <img :src="product.img" alt="" />
            </div>
            <div class="price">
              <h3>{{ setPriceConvert(product.price.basePrice) }}</h3>
              <span v-if="product.isPSU">Psu</span>
            </div>
          </div>
          <div class="product-card-form">
            <h4 v-html="product.name"></h4>

            <div class="price">
              <h3>{{ setPriceConvert(product.price.basePrice) }}</h3>
              <span v-if="product.isPSU">Psu</span>
            </div>
            <div class="hash-rate corner-dots">
              <button>Hash rate: 11.5</button>
            </div>
            <div class="form-control">
              <button class="details">Details</button>
              <button
                class="add-to-card corner-dots"
                @click="addToBasket($event, product)"
              >
                Add to card
              </button>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "OnSale",
  props: ["products", "setPriceConvert", "addToBasket"]
};
</script>
