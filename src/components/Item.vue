<template>
  <div>
    <div class="row">
      <div class="col-lg-4">
        <div class="product-image">
          <img class="image" :src="getImageUrl(item.ImageUrl)" :alt="`${item.ProductName}`" />
        </div>
      </div>
      <div class="col-lg-6">
        <div class="product-name">{{item.BrandName}}</div>
        <div class="product-description">{{item.ProductName}}</div>
        <div class="volume">1L</div>
        <div class="product-mrp">{{item.MRP}}</div>
        <div class="product-price">RS {{item.Price}}</div>
        <div class="product-add-to-cart">
          <button class="add-to-cart" @click="increase">Add To Cart</button>
          <button class="add" @click="increase">+</button>
          <div class="product-quantity">{{actualCount}}</div>
          <button class="delete" @click="decrease">-</button>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  data() {
    return {
      actualCount: this.cartcount
    };
  },
  props: {
    item: {
      type: Object
    },
    url: {
      type: String
    },
    cartcount: {
      type: Number
    }
  },
  methods: {
    increase() {
      this.actualCount++;
      this.$emit("increaseQ", this.actualCount, this.item.Price);
    },
    decrease() {
      if (this.actualCount > 0) {
        this.actualCount--;
        this.$emit("decreaseQ", this.actualCount, this.item.Price);
      }
    },
    getImageUrl(img) {
      let images = require.context("../assets/images", false, /\.jpg$/);
      return images("./" + img);
    }
  }
};
</script>

<style scoped>
.image {
  text-align: center;
  width: 200px;
  height: 200px;
}

.product-name {
  text-transform: uppercase;
  font-weight: bold;
  color: green;
  font-size: 1.25rem;
}

.product-description {
  margin-top: 10px;
  margin-bottom: 10px;
  color: #616161;
}

.product-mrp {
  text-decoration: line-through;
  font-size: 1.25rem;
  color: #616161;
}

.volume {
  color: #616161;
  font-size: 20px;
  margin-bottom: 10px;
}
.product-quantity {
  display: inline;
  margin: 0 15px;
}

.product-price {
  margin-bottom: 20px;
  margin-top: 20px;
  font-weight: 500;
  line-height: 1.2;
  color: inherit;
}

/* .container {
  width: 80%;
  margin: 0 10%;
} */

.row {
  display: flex;
  margin-bottom: 60px;
}

.add-to-cart {
  background-color: rgb(22, 172, 22);
  padding: 12px 32px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  color: white;
  cursor: pointer;
  margin-right: 35px;
}

.add,
.delete {
  background-color: rgb(22, 172, 22);
  border-radius: 50%;
  border: none;
  cursor: pointer;
  padding: 6px 10px;
  font-size: 16px;
  color: white;
}
</style>