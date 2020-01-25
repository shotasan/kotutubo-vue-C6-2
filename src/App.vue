<template>
  <div id="app">
    <product-list v-bind:products="products"></product-list>
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";

export default {
  name: "app",
  components: {
    "product-list": ProductList
  },
  data: function() {
    return {
      products: [
        {
          id: 1,
          name: "ミハエル<br>スマホ",
          price: 1580,
          image: require("./assets/image/01.jpg"),
          delv: 0,
          isSale: true
        },
        {
          id: 2,
          name: "ラルぷ<br>スマホ",
          price: 1580,
          image: require("./assets/image/02.jpg"),
          delv: 0,
          isSale: true
        },
        {
          id: 3,
          name: "ガブ<br>スマホ",
          price: 1580,
          image: require("./assets/image/03.jpg"),
          delv: 240,
          isSale: true
        },
        {
          id: 4,
          name: "ウリエル<br>スマホ",
          price: 980,
          image: require("./assets/image/04.jpg"),
          delv: 0,
          isSale: true
        },
        {
          id: 5,
          name: "アリエル<br>スマホ",
          price: 980,
          image: require("./assets/image/05.jpg"),
          delv: 0,
          isSale: false
        },
        {
          id: 6,
          name: "アズラエル<br>スマホ",
          price: 1580,
          image: require("./assets/image/06.jpg"),
          delv: 0,
          isSale: false
        }
      ]
    };
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
