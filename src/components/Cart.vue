<template>
  <div>
    <div v-for="(product,index) in products" :key="index">
      <Item
        :item="product"
        :url="product.ImageUrl"
        :cartcount="count"
        @increaseQ="incCartQty"
        @decreaseQ="decCartQty"
      ></Item>
    </div>
    <Checkout :quantity="quantity" :total="total"></Checkout>
  </div>
</template>

<script>
import Item from "./Item";
import Checkout from "./CartCheckout";
export default {
  data() {
    return {
      count: 0,
      quantity: 0,
      total: 0
    };
  },
  props: ["products"],
  components: {
    Item,
    Checkout
  },
  methods: {
    incCartQty(actualCount, itemPrice) {
      this.quantity++;
      this.total = this.total + itemPrice;
    },
    decCartQty(actualCount, itemPrice) {
      if (this.quantity > 0) {
        this.quantity--;
        this.total = this.total - itemPrice;
      }
    }
  }
};
</script>

<style scoped>
</style>