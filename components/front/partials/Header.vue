<template>
  <v-sheet height="100">

    <v-app-bar fixed color="body">
      <NuxtLink to="/">
        <v-img src="/img/logo.png" alt="logo"/>
      </NuxtLink>

      <ul class="header-menu">
        <li>
          <v-menu
              open-on-hover
              top
              offset-Y
          >
            <template v-slot:activator="{ on, attrs }">

              <a href="#"
                 v-bind="attrs"
                 v-on="on">
                Marketplace
              </a>

            </template>

            <v-list>
              <v-list-item
                  v-for="(item, index) in categories"
                  :key="index"
                  :to="`/ro/categories/${item.alias}`"
                  nuxt
              >
                <v-list-item-title>{{ item.translation.name  }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>

        </li>
        <li>
          <NuxtLink to="/ro/faq">FAQ</NuxtLink>
        </li>
        <li>
          <NuxtLink to="/ro/about">About</NuxtLink>
        </li>
      </ul>

      <v-spacer/>

      <search/>

      <NuxtLink class="button-view-1" to="/ro/plan">Upload plan</NuxtLink>

      <button class="button-view-2">Connect Wallet</button>

      <!--      <v-app-bar-nav-icon color="primary" @click.stop="drawerOne = !drawerOne"/>-->

      <!--      <cart/>-->

      <!--      <NearAuth :title="'Sign In'"/>-->

    </v-app-bar>

    <v-navigation-drawer
        v-model="drawerOne"
        fixed
        color="body"
        temporary
        width="360">
      <nav-level-one @closeDrawer="drawerOne = false" @openDrawerTwoCatalog="openDrawerTwoCatalog"
                     @openDrawerTwoCollections="openDrawerTwoCollections"/>
    </v-navigation-drawer>

    <v-navigation-drawer width="360" v-model="drawerTwo" fixed color="body" temporary>
      <nav-level-two @closeDrawerTwo="closeDrawerTwo" v-bind:items="items" v-bind:type="type"/>
    </v-navigation-drawer>

  </v-sheet>
</template>

<script>

import {mapGetters} from 'vuex'

import NavLevelOne from '@/components/front/partials/navbars/NavLeveleOne'
import NavLevelTwo from '@/components/front/partials/navbars/NavLevelTwo'
import Cart from '~/components/front/cart/CartIcon'
import NearAuth from "~/components/front/near/NearAuth";
import Search from "~/components/front/partials/Search";

export default {
  name: "Header",
  components: {
    NavLevelOne,
    NavLevelTwo,
    Cart,
    NearAuth,
    Search
  },
  computed: mapGetters({
    categories: 'getCategories',
    collections: 'getCollections',
  }),
  data() {
    return {
      drawerOne: false,
      drawerTwo: false,
      items: [],
      type: 'category'
    }
  },
  methods: {
    openDrawerTwoCollections() {
      this.items = [...this.collections]
      this.type = 'collection'
      this.drawerTwo = true
      this.drawerOne = false
    },
    openDrawerTwoCatalog() {
      this.items = [...this.categories]
      this.type = 'category'
      this.drawerTwo = true
      this.drawerOne = false
    },
    closeDrawerTwo() {
      this.drawerOne = true
      this.drawerTwo = false
    }
  }
}
</script>

<style lang="scss">
.header-menu {
  li {
    list-style: none;
    display: inline-block;
    margin-left: 30px;
  }
}
.menuable__content__active {
  top: 60px !important;
}
</style>

