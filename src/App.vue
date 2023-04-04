<template>
  <div class="container">
    <hr />
    <div class="component">
      <h1 class="title">Product Add Application</h1>

      <appNewProduct @product="addProduct"></appNewProduct>
    </div>
    <hr />

    <appProducts :productList="productList"></appProducts>
  </div>
</template>

<script>
import NewProduct from "./components/NewProduct.vue";
import Products from "./components/Products.vue";
export default {
  components: {
    appNewProduct: NewProduct,
    appProducts: Products,
  },

  data() {
    return {
      productList: [],
    };
  },

  methods: {
    addProduct(event) {
      this.productList.push(event);
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style.scss";
</style>
