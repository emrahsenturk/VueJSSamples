<template>
  <div class="container">
    <!-- <MainContainer /> -->
    <div class="cart">
      <h3>Sepet</h3>
      <ul>
        <li v-for="item in cartItems" :key="item.id">{{ item.title }}</li>
      </ul>
      <p v-if="cartItems.length == 0">Sepet boş :)</p>
    </div>
    <Product @addToCart="cartItems.push($event)" :product="product" v-for="product in productList" :key="product.id" />
  </div>
</template>

<script>
import MainContainer from "@/components/MainContainer"
import Product from "@/components/Product";
export default {
  components: {
    //MainContainer,
    Product,
  },
  data() {
    return {
      productList: [
        {
          id: 1,
          title: "MacBook Pro",
          price: 200,
          count: 0,
          description: "Açıklama 1"
        },
        {
          id: 2,
          title: "iPhone 11",
          price: 100,
          count: 100,
          description: "Açıklama 2"
        },
        {
          id: 3,
          title: "iPhone Pro Max",
          price: 150,
          count: 1000,
          description: "Açıklama 3"
        }
      ],
      cartItems: []
    };
  }
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.cart{
  margin-bottom: 10px;
}
</style>