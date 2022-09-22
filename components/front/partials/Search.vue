<template>
  <div class="banner-search-wrapper">
    <input type="text" class="search-input" @keyup="searchProduct" v-model="search">
    <button>
      <v-icon>mdi-magnify</v-icon>
    </button>

    <div class="search-area" v-if="products">
      <ul>
        <li v-for="product in products">
          <img :src="`https://back.chainlib.xyz/images/products/md/${product.main_image.src}`" alt="">
          <v-list-item :to="`/ro/categories/books-for-children/${product.alias}`">{{ product.translation.name }}</v-list-item>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

import contentApi from "~/api/contentApi";

export default {
  name: "Search",
  data() {
    return {
      search: "",
      products: null
    }
  },
  methods: {
    searchProduct() {
      this.products = null
      const data = {
        search: this.search,
        lang: 'ro',
        currency: 5
      }

      contentApi.search(data, response => {
        this.products = response
      })
    }
  }
}
</script>

<style lang="scss">
.banner-search-wrapper {
  width: 300px;
  display: flex;
  align-items: center;
  margin: 0 auto;
  position: relative;
  z-index: 999;

  input {
    border: 1px solid #EFEFEF;
    background-color: #FFF;
    display: block;
    border-radius: 20px;
    outline: none;
    width: 100%;
    height: 40px;
    padding: 10px 55px 10px 15px;
  }

  button {
    position: absolute;
    width: 50px;
    height: 40px;
    padding: 0;
    bottom: 0;
    border-left: none;
    right: 0;
    top: 0px;
  }
}

.search-area {
  position: absolute;
  background: #FFF;
  top: 50px;
  border-radius: 3px;
  width: 99%;
  z-index: 999;
  margin-left: .5%;
  ul {
    margin-bottom: 40px;
    list-style: none;
    li {
      margin-top: 10px;
      display: flex;
      align-items: center;
      img {
        height: 30px;
      }
      a {
        margin-left: 10px;
      }
    }
  }
}

@media (max-width: 1200px) {
  .banner-search-wrapper {
    width: 90%;
  }
}
</style>