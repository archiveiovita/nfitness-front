<template>
  <v-container class="footer-area mb-12">
    <v-row>
      <v-col md="6" xs="12">
        <img src="/img/logo.png" alt="">
        <div class="social-links mt-4">
          <a href="https://www.linkedin.com/in/liliana-bahnaru-810107b7" target="_blank">
            <img src="/img/linkedin.png" alt="">
          </a>
          <a href="https://discord.gg/6cMryUfBZG" target="_blank">
            <img src="/img/pngwing 1.png" alt="">
          </a>
          <a href="tel:+393487841378" target="_blank">
            <img src="/img/image 2.png" alt="">
          </a>
          <a href="mailto:nfitspace@gmail.com" target="_blank">
            <img src="/img/image 3.png" alt="">
          </a>
        </div>
      </v-col>
      <v-col md="3" xs="3" class="footer-menu">
        <ul>
          <li>
            <NuxtLink to="/ro/faq">FAQ</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/ro/plan">Upload Plan</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/ro/about">About</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/ro/contacts">Contacts</NuxtLink>
          </li>
        </ul>
      </v-col>

      <v-col cols="12" md="3" class="footer-contacts">
        <h4 class="mb-4">Keep in touch</h4>
        <p>
          Phone:
          <a href="tel:+393487841378">+393487841378</a>
        </p>
        <p>
          Mail:
          <a href="mailto:nfitspace@gmail.com">nfitspace@gmail.com</a>
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

import {mapGetters} from 'vuex';

export default {
  data: () => ({
    icons: [
      'mdi-facebook',
      'mdi-instagram',
    ],
    serviceArray: [],
  }),
  watch: {
    services() {
      this.serviceArray = []
      this.splitToChunks(this.services, 2)
    }
  },
  computed: mapGetters({
    pages: 'getPages',
    language: 'getLanguage',
    trans: 'getTranslations',
    services: 'getServices',
    categories: 'getCategories',
  }),
  mounted() {
    this.splitToChunks(this.services, 2)
  },
  methods: {
    splitToChunks(array, parts) {
      const services = []
      array.forEach(service => services.push(service))
      for (let i = parts; i > 0; i--) {
        this.serviceArray.push(services.splice(0, Math.ceil(services.length / i)))
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.footer {
  background: #FFF;
  padding-bottom: 60px;

  .v-expansion-panel {
    box-shadow: none !important;
    background: $bcg-header !important;
    font-family: $font-roboto;

    &:before {
      box-shadow: none;
    }
  }

  .v-expansion-panel-header {
    font-size: 20px !important;
    color: $main-color;
    padding-left: 0;
    padding-right: 0;
  }

  .v-expansion-panel-content__wrap {
    padding-left: 0 !important;
    padding-right: 0 !important;
  }

  a {
    font-size: 18px;
    color: #FFF;
    display: block;
    line-height: 1.8;
    font-weight: 300;
    font-family: $font-roboto, sans-serif;
  }

  p {
    font-family: $font-roboto, sans-serif;
    font-size: 18px;
    color: #FFF;
    letter-spacing: 0;
    line-height: 1.5;
    margin-bottom: 10px;
    font-weight: 300;
  }

  &__desktop {
    display: none;
  }
}

@media (max-width: 1200px) {
  .footer {
    padding: 15px !important;
  }
  .footer__logo {
    .v-image {
      width: 80% !important;
    }
  }
}

.footer-social-link {
  display: inline-block !important;
}
.footer__subtitle {
  font-family: $font-roboto, sans-serif;
  font-size: 20px;
  color: #e9642d;
  letter-spacing: 0;
  line-height: 20px;
  font-weight: 400;
  margin-bottom: 20px;
}
a {
  font-family: $font-roboto;
  text-transform: capitalize;
}
</style>
