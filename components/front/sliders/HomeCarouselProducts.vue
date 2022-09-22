<template>
  <div class="h-slider">

    <VueSlickCarousel ref="homeCarousel"
                      :infinite="false"
                      :variableWidth="true"
                      :arrows="false"
                      :settings="localSettings">
      <div class="h-slider__item" v-for="(product, i) in products" :key="i" v-if="product.main_image">
        <div class="h-slider__item-inner">
          <nuxt-link :to="`/ro/categories/${category.alias}/${product.alias}`">
            <div class="h-slider__image">
              <img :src="`https://back.chainlib.xyz/images/products/sm/${product.main_image.src}`">
            </div>
          </nuxt-link>

          <div class="product-description">
            <h3>{{ product.translation.name }}</h3>

            <div class="product-price">
              <p>10 Near</p>
              <span>1 of 514</span>
            </div>

            <div class="product-params">
              <span>Belly sport</span>
              <span>Noel Munkey</span>
              <span>Pennyatwork</span>
            </div>
          </div>
        </div>
      </div>
    </VueSlickCarousel>

    <div class="custom-arrow next-slide" @click="nextSlide">
      <v-btn icon color="primary">
        <arrow-left/>
      </v-btn>
    </div>
    <div class="custom-arrow prev-slide" @click="prevSlide">
      <v-btn icon color="primary">
        <arrow-left/>
      </v-btn>
    </div>
  </div>
</template>

<script>

import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import VueSlickCarousel from 'vue-slick-carousel'
import ArrowLeft from '@/components/front/sliders/ArrowLeft.vue'

export default {
  name: 'HomeCarousel',
  props: ['products', 'category'],
  components: {
    VueSlickCarousel,
    ArrowLeft
  },
  data() {
    return {
      hover: true,
      localSettings: {
        dots: false,
        slidesToScroll: 1,
        slidesToShow: 1,
        arrows: false,
        infinite: true
      }
    }
  },
  methods: {
    nextSlide() {
      this.$refs.homeCarousel.next()
    },
    prevSlide() {
      this.$refs.homeCarousel.prev()
    }
  }
}
</script>

<style lang="scss" scoped>
.h-slider {
  .product-description {
    h3 {
      margin-bottom: 20px;
      color: #000;
      font-size: 18px;
      text-align: left;
    }
  }

  &__item {
    position: relative;
    display: block;
    padding: 25px 16px;

    &-inner {
      display: block;
      background-color: #FFF;
      color: #000;
      padding: 25px;
      width: 100%;
      border-radius: 20px;
    }

    .v-btn {
      background: $bcg-butt;
      margin-bottom: 20%;
    }
  }

  &__actions {
    position: absolute;
    z-index: 1;
  }

  &__image {
    img {
      width: 100%;
      border-radius: 20px;
    }
  }

  .next-slide {
    transform: rotate(180deg);
  }

  .product-price {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #F4F4F4;

    span {
      display: block;
      color: #838383;
    }

    p {
      color: #00AC4F;
      font-size: 16px;
    }
  }

  .product-params {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    span {
      border-radius: 20px;
      background-color: #f5f5f5;
      color: #5539A8;
      padding: 10px;
      font-size: 12px;
    }
  }
}

@media (min-width: 1200px) {
  .h-slider {
    &__actions {
      display: none;
    }
  }
}

.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: .5;
  position: absolute;
  width: 100%;
}
</style>
