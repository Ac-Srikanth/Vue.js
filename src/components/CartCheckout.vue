<template>
  <div class="cart-container">
    <div class="cart-quantity">
      Quantity:
      <span>{{quantity}}</span>
    </div>
    <div>
      TOTAL:
      <span>{{total}}</span>
    </div>
    <div>
      <button class="cart-checkout">Checkout</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["quantity", "total"]
};
</script>

<style scoped>
.cart-checkout {
  background-color: rgb(22, 172, 22);
  padding: 12px 32px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  color: white;
  cursor: pointer;
  margin-right: 35px;
}

cart-quantity {
  text-transform: uppercase;
}

.cart-container {
  margin-top: 20px;
  background-color: plum;
  display: flex;
  padding-bottom: 40px;
  padding-top: 5px;
  justify-content: space-evenly;
  position: fixed;
  top: 550px;
  left: 0;
  width: 100%;
}
</style>