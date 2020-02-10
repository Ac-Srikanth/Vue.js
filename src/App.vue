<template>
  <div id="app">
    <Cart :products="products"></Cart>
  </div>
</template>

<script>
import Product from "./assets/JSON/productList.json";
import Cart from "./components/Cart";
export default {
  name: "app",
  data() {
    return {
      products: Product
    };
  },
  components: {
    Cart
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
