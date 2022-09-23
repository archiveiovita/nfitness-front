<template>
  <div class="faq">

    <v-container>
      <v-row>
        <v-col class="col-md-12 col-12">
          <h1>FAQ</h1>
        </v-col>

        <v-col class="col-md-12 col-12">
          <p>
            1. Ask The Trainers is a free remote information support service that provides answers to the user's
            questions, pointing/directing to the information resources in the NFiTNESS Ecosystem
          </p>
          <p>
            2. The Trainers answer users' any questions regarding the needs for train & earn, offering them:
          </p>
          <ul>
            <li>general information about NFiTNESS Ecosystem</li>
            <li>information about train & earn concept</li>
            <li>information about workout/meal plans as NFT</li>
          </ul>
        </v-col>

        <v-row justify="center" align="center">
          <v-col class="col-md-9 col-10">
            <form class="text-center mt-8">
              <v-text-field
                  dense outlined
                  v-model="name"
                  :error-messages="nameErrors"
                  :counter="10"
                  label="Name"
                  required
                  @input="$v.name.$touch()"
                  @blur="$v.name.$touch()"
              ></v-text-field>
              <v-text-field
                  dense outlined
                  v-model="email"
                  :error-messages="emailErrors"
                  label="E-mail"
                  required
                  @input="$v.email.$touch()"
                  @blur="$v.email.$touch()"
              ></v-text-field>
              <v-textarea
                  dense outlined
                  v-model="question"
                  :error-messages="questionErrors"
                  :counter="120"
                  label="Question"
                  required
                  @input="$v.question.$touch()"
                  @blur="$v.question.$touch()"
              ></v-textarea>
              <v-btn
                  class="mr-4"
                  @click="submit"
                  color="#3D00B7"
                  dark
              >
                submit
              </v-btn>
            </form>
          </v-col>
        </v-row>

        <v-col class="col-md-12">
          <v-alert
              color="#BBB"
              icon="mdi-chat-question-outline"
              dense
              prominent
              class="faq-question"
              shaped
          >
            How do I upload a workout/meal plan?
            <span>01-20-2022</span>
          </v-alert>
          <v-alert
              color="#ededed"
              icon="mdi-forum"
              prominent
              class="faq-answer"
              shaped
          >
            In the topbar click the button "Upload plan", fill out the form, upload the images and here You go!
          </v-alert>
        </v-col>
        <v-col class="col-md-12">
          <v-alert
              color="#BBB"
              icon="mdi-chat-question-outline"
              dense
              prominent
              class="faq-question"
              shaped
          >
            Is there any train & earn program working?
            <span>03-06-2022</span>
          </v-alert>
          <v-alert
              color="#ededed"
              icon="mdi-forum"
              prominent
              class="faq-answer"
              shaped
          >
            The marketplace allows fitness trainers to upload their workout/meal plans and mint them as NFTs. Users can
            buy these NFTs, mint out of them new NFTs, by adding to them the experience of their usage and resell them.
          </v-alert>
        </v-col>
        <v-col class="col-md-12">
          <v-alert
              color="#BBB"
              icon="mdi-chat-question-outline"
              dense
              prominent
              class="faq-question"
              shaped
          >
            Hi. Is it possible to buy the workout/meal plans as NFT?
            <span>26-05-2022</span>
          </v-alert>
          <v-alert
              color="#ededed"
              icon="mdi-forum"
              prominent
              class="faq-answer"
              shaped
          >
            Yes, in future. The NFT functionality is under development
          </v-alert>
        </v-col>

      </v-row>
    </v-container>
  </div>
</template>

<script>
import {validationMixin} from 'vuelidate'
import {required, maxLength, email} from 'vuelidate/lib/validators'
import Search from "~/components/front/partials/Search";

export default {
  components: {Search},
  mixins: [validationMixin],

  validations: {
    name: {required, maxLength: maxLength(10)},
    email: {required, email},
    question: {required, maxLength: maxLength(120)}
  },

  data: () => ({
    name: '',
    email: '',
    question: ''
  }),

  computed: {
    nameErrors() {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
      !this.$v.name.required && errors.push('Name is required.')
      return errors
    },
    emailErrors() {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push('Must be valid e-mail')
      !this.$v.email.required && errors.push('E-mail is required')
      return errors
    },
    questionErrors() {
      const errors = []
      if (!this.$v.question.$dirty) return errors
      !this.$v.question.maxLength && errors.push('Question must be at most 120 characters long')
      !this.$v.question.required && errors.push('Question is required')
      return errors
    },
  },

  methods: {
    submit() {
      this.$v.$touch()
    },
    clear() {
      this.$v.$reset()
      this.name = ''
      this.email = ''
      this.question = ''
    },
  },
}
</script>

<style lang="scss">
.faq {
  margin-top: -60px;

  h1 {
    text-align: center;
  }

  .faq-question {
    font-weight: 400;
    font-size: 17px;
    color: #363636;
    letter-spacing: 0.22px;
    line-height: 30px;
    padding: 30px;
    margin-top: 15px;
    font-style: italic;
    position: relative;

    span {
      position: absolute;
      display: inline-block;
      right: 15px;
      color: #3D00B7;
      border: 1px solid #3D00B7;
      border-radius: 5px;
      padding: 3px;
      font-style: normal;
      font-weight: 500;
      font-size: 15px;
    }
  }

  .faq-answer {
    font-weight: 400;
    font-size: 18px;
    color: #363636;
    letter-spacing: 0.22px;
    line-height: 30px;
    padding: 30px;
    margin-bottom: 15px;
  }

  .v-alert--prominent .v-alert__icon.v-icon {
    color: #3D00B7 !important;
  }
}
</style>