<template>

  <div class="category-page-area">
    <v-container>
      <v-row>
        <v-col>
          <h2 class="text-center mt-3 mb-4">{{ category.translation.name }}</h2>
        </v-col>
      </v-row>
      <v-row>
        <v-col md="4" cols="12" class="products-view-1" v-for="(item, key) in products" :key="key">
          <div class="product-view-1">
            <!--            <img src="/img/unsplash_F56Y7dgrAkc.png" alt="">-->
            <nuxt-link :to="`/ro/categories/${category.alias}/${item.product.alias}`" class="product">
              <img v-if="item.product.main_image"
                   :src="`https://back.chainlib.xyz/images/products/md/${item.product.main_image.src}`" alt="">
            </nuxt-link>
            <v-row class="details">
              <v-col cols="9" md="" style="background-image: url('/img/Ellipse 95.png')" class="product-title">
                <h4>
                  <nuxt-link :to="`/ro/categories/${category.alias}/${item.product.alias}`" class="product">
                    <span v-if="item.product.translation.name.length > 23">
                      {{ item.product.translation.name.slice(0, 23) }}...
                    </span>
                    <span v-else>
                      {{ item.product.translation.name }}
                    </span>
                  </nuxt-link>
                </h4>
                <p>3 plans, 124 exercices</p>
              </v-col>
              <v-col cols="3" md="3" class="product-price text-right">
                <span>Highest Bid</span>
                <p>0.25 NEAR</p>
              </v-col>
            </v-row>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
  <!--  <div class="h-content">-->
  <!--    <v-container v-if="category">-->

  <!--      &lt;!&ndash;      <v-navigation-drawer v-model="filterModal" fixed color="body" temporary>&ndash;&gt;-->
  <!--      &lt;!&ndash;        <filter-modal @closeFilterModal="closeFilterModal" :category="category"/>&ndash;&gt;-->
  <!--      &lt;!&ndash;      </v-navigation-drawer>&ndash;&gt;-->

  <!--      &lt;!&ndash;      <v-navigation-drawer v-model="sortModal" fixed color="body" temporary>&ndash;&gt;-->
  <!--      &lt;!&ndash;        <sort-modal @closeSortModal="closeSortModal" :category="category"/>&ndash;&gt;-->
  <!--      &lt;!&ndash;      </v-navigation-drawer>&ndash;&gt;-->

  <!--      <v-row>-->
  <!--        <v-col cols="12">-->
  <!--          <h1 class="text-center mt-3">{{ category.translation.name }}</h1>-->
  <!--        </v-col>-->

  <!--        <v-col class="col-12">-->

  <!--          <div class="category-container">-->
  <!--            &lt;!&ndash;                        <div class="filter">&ndash;&gt;-->
  <!--            &lt;!&ndash;                          <v-btn large @click="openFilterModal">&ndash;&gt;-->
  <!--            &lt;!&ndash;                            <v-icon color="title" class="mr-2">mdi-filter</v-icon>&ndash;&gt;-->
  <!--            &lt;!&ndash;                            Filter&ndash;&gt;-->
  <!--            &lt;!&ndash;                          </v-btn>&ndash;&gt;-->
  <!--            &lt;!&ndash;                          <v-btn large @click="openSortModal">&ndash;&gt;-->
  <!--            &lt;!&ndash;                            <v-icon color="title" class="mr-2">mdi-sort</v-icon>&ndash;&gt;-->
  <!--            &lt;!&ndash;                            Sort&ndash;&gt;-->
  <!--            &lt;!&ndash;                          </v-btn>&ndash;&gt;-->
  <!--            &lt;!&ndash;                        </div>&ndash;&gt;-->

  <!--            <v-row>-->

  <!--              <v-col class="col-lg-12 col-12 mb-2"-->
  <!--                     v-for="(item, key) in products"-->
  <!--                     :key="key">-->

  <!--                <v-row class="product-item-wrapper">-->

  <!--                  <v-col class="col-lg-9 col-12 mb-2">-->
  <!--                    <h2 class="mb-8 product-name">-->
  <!--                      <nuxt-link :to="`/ro/categories/${category.alias}/${item.product.alias}`" class="product">-->
  <!--                        {{ item.product.translation.name }}-->
  <!--                      </nuxt-link>-->
  <!--                    </h2>-->
  <!--                    <nuxt-link :to="`/ro/categories/${category.alias}/${item.product.alias}`" class="product mobile-only mb-4">-->
  <!--                      <v-img v-if="item.product.main_image"-->
  <!--                          :src="`https://back.chainlib.xyz/images/products/sm/${item.product.main_image.src}`"></v-img>-->
  <!--                    </nuxt-link>-->
  <!--                    <p class="product-description mb-8" v-if="item.product.translation.body" v-html="item.product.translation.body.substring(0,525)+'...'"></p>-->
  <!--                    <div class="product-properties-list">-->
  <!--                      <div class="product-properties-item"-->
  <!--                           v-for="(property, key) in filterProperties(item.properties)"-->
  <!--                           :key="key">-->
  <!--                        <b>{{ key }}:</b> {{ property }}-->
  <!--                      </div>-->
  <!--                    </div>-->

  <!--                    <v-row>-->
  <!--                      <v-col>-->
  <!--                        &lt;!&ndash;                        <div class="collectionOne__price price">&ndash;&gt;-->
  <!--                        &lt;!&ndash;                          <span>{{ item.product.personal_price.price }}</span>&ndash;&gt;-->
  <!--                        &lt;!&ndash;                          <span&ndash;&gt;-->
  <!--                        &lt;!&ndash;                              v-if="item.product.personal_price.old_price > item.product.personal_price.price">/</span>&ndash;&gt;-->
  <!--                        &lt;!&ndash;                          <span class="price__discount"&ndash;&gt;-->
  <!--                        &lt;!&ndash;                                v-if="item.product.personal_price.old_price > item.product.personal_price.price">&ndash;&gt;-->
  <!--                        &lt;!&ndash;                              {{ item.product.personal_price.old_price }}&ndash;&gt;-->
  <!--                        &lt;!&ndash;                        </span>&ndash;&gt;-->
  <!--                        &lt;!&ndash;                          <span>{{ currency.abbr }}</span>&ndash;&gt;-->
  <!--                        &lt;!&ndash;                        </div>&ndash;&gt;-->
  <!--                      </v-col>-->
  <!--                      &lt;!&ndash;                      <v-col>&ndash;&gt;-->
  <!--                      &lt;!&ndash;                        <near-buy-sub-product-btn :product="item.product"></near-buy-sub-product-btn>&ndash;&gt;-->
  <!--                      &lt;!&ndash;                      </v-col>&ndash;&gt;-->
  <!--                    </v-row>-->

  <!--                  </v-col>-->

  <!--                  <v-col class="col-lg-3 col-12 mb-2 desktop-only">-->
  <!--                    <nuxt-link :to="`/ro/categories/${category.alias}/${item.product.alias}`" class="product">-->
  <!--                      <v-img v-if="item.product.main_image"-->
  <!--                          :src="`https://back.chainlib.xyz/images/products/sm/${item.product.main_image.src}`"></v-img>-->
  <!--                    </nuxt-link>-->
  <!--                  </v-col>-->

  <!--                </v-row>-->


  <!--              </v-col>-->
  <!--            </v-row>-->

  <!--          </div>-->
  <!--        </v-col>-->
  <!--      </v-row>-->

  <!--    </v-container>-->
  <!--  </div>-->
</template>

<script>

import {mapGetters} from 'vuex'
import contentApi from '@/api/contentApi'
import FilterModal from '@/components/front/productWidgets/FilterModal.vue'
import SortModal from '@/components/front/productWidgets/SortModal.vue'
import NearBuyProductBtn from "~/components/front/near/NearBuyProductBtn"
import Search from "~/components/front/partials/Search";

export default {
  components: {FilterModal, SortModal, NearBuyProductBtn, Search},
  async asyncData({app, params, store}) {
    let categ = null;
    let products = null;
    await contentApi.getMarketplaceCategory({
      lang: store.state.lang.lang,
      alias: params.slugCategory,
      currency: store.state.currency.id
    }, data => {
      categ = data.category
      products = data.products
    })
    return {
      category: categ,
      products: products
    }
  },
  watch: {
    async currency() {
      await contentApi.getMarketplaceCategory({
            lang: this.language.lang,
            alias: this.category.alias,
            currency: this.currency.id
          },
          data => {
            this.category = data
            this.products = this.category.products
          }
      )
    },
  },
  data() {
    return {
      category: null,
      filterModal: false,
      sortModal: false,
    }
  },
  computed: mapGetters({
    categories: 'getCategories',
    language: 'getLanguage',
    currency: 'getCurrency',
    trans: 'getTranslations',
  }),
  async mounted() {
    this.$nuxt.$on('replaceProducts', data => {
      this.products = data
    })

    this.$nuxt.$on('resetFilter', () => {
      contentApi.getMarketplaceCategory({
        lang: this.language.lang,
        alias: this.category.alias,
        currency: this.currency.id
      }, data => {
        this.category = data
        this.products = this.category.products
      })
    })
  },
  methods: {
    filterProperties(properties) {
      return Object.assign(
          ...Object
              .keys(properties)
              .slice(0, 4)
              .map(k => ({[k]: properties[k]}))
      );
    },
    openFilterModal() {
      this.filterModal = true
    },
    closeFilterModal() {
      this.filterModal = false
    },
    openSortModal() {
      this.sortModal = true
    },
    closeSortModal() {
      this.sortModal = false
    }
  }
}
</script>

<style lang="scss">

</style>