<template>
  <div>
    <v-container>
      <v-row class="main-area">
        <v-col md="6" cols="12">
          <h2>Train and Earn with the best NFT workout </h2>
          <p>Find the best workout/meal plans that suit You. Use it and write down Your experience and recommendations
            for
            the next users. Now You can sell it! You'll be paid royalties each time a plan with Your training experience
            will be sold by one user to another. Train & Earn! </p>
          <button class="button-view-1">Try Now</button>
          <v-row class="ratings">
            <v-col md="3" cols="4">
              <h4>98k</h4>
              <p>Workouts</p>
            </v-col>
            <v-col md="3" cols="4">
              <h4>12k</h4>
              <p>Auction</p>
            </v-col>
            <v-col md="3" cols="4">
              <h4>15k</h4>
              <p>Trainers</p>
            </v-col>
          </v-row>
        </v-col>
        <v-col md="6" cols="12">
          <img src="/img/1stgroup.png" alt="">
        </v-col>
      </v-row>
    </v-container>

    <div class="mint-buy-wrapper">
      <v-container>
        <v-row class="mint-buy-area">
          <v-col md="5" cols="12">
            <h4>The NFT workout or meal plans price will increase the more times is used</h4>
          </v-col>
          <v-col md="7" cols="12">
            <v-row>
              <v-col md="6" cols="12">
                <h5 style="background-image: url('/img/card-tick-1 1.png')">
                  Buy and train
                </h5>
                <p>Try the NFT workout/meal plan and add to NFT your experience and recommendations for the next users
                  (add excercisez/meals/notes, etc.)</p>
              </v-col>
              <v-col md="6" cols="12">
                <h5 style="background-image: url('/img/chart-square 2.png')">
                  Mint and earn
                </h5>
                <p>Mint the NFT workout/meal plan with Your experience and sell it at a higher price. You'll be paid
                  each time this plan with Your training experience will be sold to a next user</p>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </div>

    <v-container>
      <v-row class="create-own-area">
        <v-col md="3" cols="12">
          <h5>
            Create your
            <span>collection</span>
            of the best workout
            or meal plans
            <span>collection</span>
          </h5>
        </v-col>
        <v-col md="9" cols="12" class="products-view-1">
          <v-row>

            <v-col md="7" cols="12">
              <div class="product-view-1">
                <nuxt-link to="" class="product">
                  <img src="/img/unsplash_F56Y7dgrAkc.png" alt="">
                </nuxt-link>
                <v-row class="details">
                  <v-col cols="9" md="" style="background-image: url('/img/Ellipse 95.png')" class="product-title">
                    <h4>
                      <nuxt-link to="" class="product">
                        Full Body Workout
                      </nuxt-link>
                    </h4>
                    <p>3 plans, 124 exercices</p>
                  </v-col>
                  <v-col cols="3" md="3" class="product-price text-right">
                    <span>Highest Bid</span>
                    <p>0.25 ETH</p>
                  </v-col>
                </v-row>
              </div>
            </v-col>

            <v-col md="5" cols="12">

              <v-row class="product-view-2">
                <v-col md="6" cols="6">
                  <img src="/img/Group 88.png" alt="">
                </v-col>
                <v-col cols="6" md="6" class="details">
                  <h4>Full Body Workout</h4>
                  <span class="product-price" style="background-image: url('/img/Ellipse 95.png')">0.25 ETH</span>
                </v-col>
              </v-row>

              <v-row class="product-view-2">
                <v-col md="6" cols="6">
                  <img src="/img/unsplash_Tyg0rVhOTrE.png" alt="">
                </v-col>
                <v-col cols="6" md="6" class="details">
                  <h4>Full Body Workout</h4>
                  <span class="product-price" style="background-image: url('/img/Ellipse 95.png')">0.25 ETH</span>
                </v-col>
              </v-row>

              <v-row class="product-view-2">
                <v-col md="6" cols="6">
                  <img src="/img/unsplash_wHJ5L9KGTl4.png" alt="">
                </v-col>
                <v-col cols="6" md="6" class="details">
                  <h4>Full Body Workout</h4>
                  <span class="product-price" style="background-image: url('/img/Ellipse 95.png')">0.25 ETH</span>
                </v-col>
              </v-row>

            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>

    <v-container>
      <v-row class="add-training-area">
        <v-col md="6" cols="12">
          <img src="/img/Group300.png" alt="">
        </v-col>
        <v-col md="6" cols="12">
          <h4>Add Your training experience to Collection and sell it as NFT at a higher price</h4>
          <p>You can buy I.E. a Meal plan, a Pushups plan and an Abs plan from different trainers; combine them into one
            workout/meal plans collection; add to it Your experience; sell it at a much higher price to another user;
            receive royalty from each sale of workout/meal plans collection plan in future.</p>
          <button class="button-view-1">Explore Plans</button>
        </v-col>
      </v-row>
    </v-container>

    <div class="plans-area">

      <v-container>
        <h3>Workout and meal PLANS </h3>

        <div class="h-content">

          <div class="h-sections">

            <section class="h-section" v-for="(item, index) in items" :key="index" v-if="item.view.products.length">

              <h2 class="h-section__title">
                {{ item.view.translation.name }}
              </h2>

              <home-carousel-products :products="item.view.products" :category="item.view"/>

              <div class="h-section__button">

                <NuxtLink :to="`/${language.lang}/categories/${item.view.alias}`"
                          class="button-view-2 button-customize">
                  View all
                </NuxtLink>

              </div>

            </section>

          </div>

        </div>
      </v-container>
    </div>

  </div>

</template>

<script>

import {mapGetters} from 'vuex'
import HomeCarouselSets from '@/components/front/sliders/HomeCarouselSets.vue'
import HomeCarouselProducts from '@/components/front/sliders/HomeCarouselProducts.vue'
import HomeBannerCarousel from '@/components/front/sliders/HomeBannerCarousel.vue'

export default {
  components: {HomeBannerCarousel, HomeCarouselSets, HomeCarouselProducts},
  computed: mapGetters({
    categories: 'getCategories',
    collections: 'getCollections',
    language: 'getLanguage'
  }),
  data() {
    return {
      items: null
    }
  },
  mounted() {
    const items = []
    this.categories.forEach((category, i) => {
      if (category.on_home === 1) {
        items.push({type: 'category', view: category})
      }
    })
    this.items = items
  }
}
</script>

<style lang="scss">
.h-section__title {
  color: #ED6D5E;
  font-weight: 500;
  text-transform: uppercase;
  font-size: 30px;
}

.button-customize {
  background-color: #FFF !important;
}
</style>