<template>
  <div>
    <div v-for="(song, index) in songs" :key="index">
      <header>{{ song.title }}</header>
      <h1>{{ song.lyrics }}</h1>
    </div>
    <!-- <template v-for="(song, index) in songs">
      <header :key="index">{{ song.title }}</header>
      <h1 :key="index">{{ song.lyrics }}</h1>
    </template>-->
    <div class="container">
      <product-header
        v-bind:count="filterdList.length"
        v-bind:showSaleItem="showSaleItem"
        v-bind:showDelvFree="showDelvFree"
        v-bind:sortOrder="sortOrder"
        v-on:showSaleItemChanged="showSaleItem = !showSaleItem"
        v-on:showDelvFreeChanged="showDelvFree = !showDelvFree"
        v-on:sortOrderChanged="sortOrderChanged"
      ></product-header>
      <div class="list">
        <product v-for="product in filterdList" v-bind:product="product" v-bind:key="product.id"></product>
      </div>
    </div>
  </div>
</template>

<script>
import productHeader from "./productHeader.vue";
import product from "./product.vue";

export default {
  components: {
    "product-header": productHeader,
    product: product
  },
  props: ["products"],
  data: function() {
    return {
      showSaleItem: false,
      showDelvFree: false,
      sortOrder: 1,
      songs: [
        {
          title: "赤とんぼ",
          lyrics: "ゆうやけこやけの赤とんぼ",
          composer: "山田工作"
        },
        {
          title: "紫とんぼ",
          lyrics: "ゆう毛やこんやけ",
          composer: "山田山"
        },
        {
          title: "黄色とんぼ",
          lyrics: "ボンとかあの毛や苔熊野",
          composer: "山田太郎"
        }
      ]
    };
  },
  methods: {
    sortOrderChanged: function(order) {
      this.sortOrder = order;
    }
  },
  computed: {
    filterdList: function() {
      var newList = [];
      for (var i = 0; i < this.products.length; i++) {
        var isShow = true;

        if (this.showSaleItem && !this.products[i].isSale) {
          isShow = false;
        }

        if (this.showDelvFree && this.products[i].delv > 0) {
          isShow = false;
        }

        if (isShow) {
          newList.push(this.products[i]);
        }
      }
      if (this.sortOrder == 1) {
        // 並び替え済み
      } else if (this.sortOrder == 2) {
        newList.sort(function(a, b) {
          return a.price - b.price;
        });
      }
      return newList;
    }
  }
};
</script>

<style scoped>
.container {
  width: 960px;
  margin: 0 auto;
}

.list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.list::after {
  content: "";
  display: block;
  width: 250px;
}
</style>