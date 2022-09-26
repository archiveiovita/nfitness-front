<template>
  <div class="about">

    <v-container>
      <div class="about-headings">
        <h1>NFiTNESS Marketplace</h1>
        <h3>The first P2P fitness blockchain marketplace based on the collective experience</h3>
      </div>

      <v-row>
        <v-col class="col-md-6">
          <v-img src="/img/About-1.png" alt="" height="520px"></v-img>
        </v-col>
        <v-col class="col-md-6">
          <v-img src="/img/About-2.png" alt="" height="520px"></v-img>
        </v-col>

        <v-col class="col-md-12">
          <h2>About the Project</h2>
          <p class="text-center">
            The marketplace allows fitness trainers to upload their workout/meal plans and mint them as NFTs. <br>
            Users can buy these NFTs, mint out of them new NFTs, by adding to them the experience of their usage, and
            resell them. The more experience of using a workout/meal plan users attach, the more valuable and expensive
            it becomes. The more royalty the trainer and previous owners get from each transaction.
          </p>
          <h2>NFiTNESS Trainers/Coaches</h2>
        </v-col>

        <v-col class="col-md-5">
          <img src="/img/Coach-1.png" height="669px">
        </v-col>
        <v-col class="col-md-7">
          <img src="/img/Coach-2.png">
        </v-col>

        <v-col class="col-md-12">
          <h2>EXAMPLES OF WORKOUT/MEAL PLANS ON NFiTNESS</h2>
        </v-col>

        <v-col class="col-md-3">
          <v-img src="/img/plan-1.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-2.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-3.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-4.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-5.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-6.png" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-7.jpeg" height="280px"></v-img>
        </v-col>
        <v-col class="col-md-3">
          <v-img src="/img/plan-8.jpeg" height="280px"></v-img>
        </v-col>

        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/img/plan-1.png"></v-img>-->
        <!--        </v-col>-->
        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/About-section-3-works-image-4.jpeg"></v-img>-->
        <!--        </v-col>-->
        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/About-section-3-works-image-5.jpeg"></v-img>-->
        <!--        </v-col>-->
        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/About-section-3-works-image-6.jpeg"></v-img>-->
        <!--        </v-col>-->
        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/About-section-3-works-image-7.jpeg"></v-img>-->
        <!--        </v-col>-->
        <!--        <v-col class="col-md-3">-->
        <!--          <v-img src="/About-section-3-works-image-8.jpeg"></v-img>-->
        <!--        </v-col>-->
      </v-row>
    </v-container>

  </div>
</template>

<script>
import {mapGetters} from 'vuex'

export default {
  layout: "default",
  head() {
    return {
      title: 'NFITNESS About',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.description
        }
      ]
    }
  },
  data: () => ({
    title: '',
    description: '',
  }),
  computed: mapGetters({
    trans: 'getTranslations'
  }),
  mounted() {
    this.title = this.$trans('PageNames', 'aboutSeoTitle')
    this.description = this.$trans('PageNames', 'aboutSeoDesc')
  }
}
</script>

<style lang="scss">
.about {
  margin-top: -60px;

  .about-headings {
    text-align: center;
    max-width: 800px;
    margin: 0 auto;

    h3 {
      margin: 20px 0;
    }
  }

  h2 {
    text-align: center;
    font-size: 36px;
    color: #363636;
    margin: 20px 0;
  }
}
</style>
