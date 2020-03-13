<template>
  <div
    :class="
      isBasketActive
        ? 'basket-wrapper active clearfix'
        : 'basket-wrapper clearfix'
    "
  >
    <button class="cross" @click="setActiveBasket"></button>
    <h3>{{ setBasketListsValue }}</h3>
    <div class="products-list-wrapper">
      <ul :class="checkBasketSize">
        <li v-for="(product, id) in basket" :key="id">
          <div class="image-wrapper corner-dots">
            <button @click="removeProduct(product, id)">
              <img :src="product.img" class="product-image" alt="" />
              <img
                src="/assets/imgs/base-icons/trash.svg"
                class="trash"
                alt=""
              />
            </button>
          </div>
          <h4>{{ product.name }}</h4>
          <div class="control-and-price">
            <button @click="removeOne(product)"></button>
            <span>{{
              product.counter >= 10 ? product.counter : `0${product.counter}`
            }}</span>
            <button @click="addOne(product)"></button>
            <h4>{{ product.price.basePrice }}.00$</h4>
          </div>
        </li>
      </ul>
    </div>
    <div class="next-step">
      <button class="corner-dots">Continue</button>
      <button @click="removeBasketList" class="corner-dots">Remove all</button>
      <span class="price">{{ `$${setFullPrice}.00` }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["isBasketActive", "setActiveBasket", "basket", "removeBasketList"],
  updated() {
    //remove <br/> tag from Product Name
    this.basket.forEach((product, index) => {
      this.basket[index].name = product.name.replace("<br/>", " ");
    });
  },
  methods: {
    addOne(product) {
      product.counter++;
    },
    removeOne(product) {
      if (product.counter > 1) {
        product.counter--;
      }
    },

    removeProduct(product, id) {
      product.counter = 0;
      console.log(product);
      this.$delete(this.basket, id);
    }
  },
  computed: {
    setBasketListsValue: function() {
      switch (this.basket.length) {
        case 0:
          return `You card is empty`;
        case 1:
          return `You have 1 item in you card`;
        default:
          return `You have ${this.basket.length} items in you card`;
      }
    },
    setFullPrice: function() {
      let fullPrice = 0;
      if (this.basket) {
        this.basket.forEach(
          product => (fullPrice += product.price.basePrice * product.counter)
        );
      }
      return fullPrice;
    },
    checkBasketSize: function() {
      return this.basket.length > 3
        ? "products-list scrollable"
        : "products-list";
    }
  },
  watch: {}
};
</script>
