<template>
  <v-container grid-list-xl>
    <v-layout row justify-center align-center wrap class="mt-4 pt-2">
      <v-flex xs12 sm12 md6 lg6 xl6>
        <h2 class="pb-4 mt-2">
          <span>GetIn</span>
          <span class="pink--text">Touch</span>
        </h2>
        <div class="py-4 subheading font-weight-bold">
          <v-icon large color="pink" left>
            fas fa-map-marker-alt
          </v-icon>
          <span>Austin, Texas</span>
        </div>
        <div class="py-4 subheading font-weight-bold">
          <v-icon large color="pink" left>
            fas fa-envelope
          </v-icon>
          <span>marcelomendonca84@gmail.com</span>
        </div>
        <div class="py-4 subheading font-weight-bold">
          <v-icon large color="pink" left>
            fab fa-linkedin-in
          </v-icon>
          <a
            class="pink--text"
            href="https://www.linkedin.com/in/marcelo-mendonca-data-analytics/"
          >
            Marcelo Mendonca
          </a>
        </div>
        <!-- <div class="py-4 subheading font-weight-bold">
          <v-icon large color="pink" left>fas fa-check</v-icon>
          <span>Freelance</span>
          <span class="pink--text">Available</span>
        </div> -->
      </v-flex>

      <v-flex xs12 sm12 md6 lg6 xl6>
        <h2 class="pb-4 mb-4">
          <span>Contact</span>
          <span class="pink--text">Form</span>
        </h2>

        <form method="POST" action="https://formspree.io/xdowweee">
          <v-text-field
            v-model="name"
            name="name"
            color="pink"
            background-color="transparent"
            :error-messages="nameErrors"
            label="Name"
            required
            @blur="$v.name.$touch()"
          />
          <v-text-field
            v-model="email"
            type="email"
            color="pink"
            background-color="transparent"
            name="email"
            :error-messages="emailErrors"
            label="E-mail"
            required
            @blur="$v.email.$touch()"
          />
          <v-textarea
            v-model="body"
            color="pink"
            background-color="transparent"
            :counter="200"
            :error-messages="bodyErrors"
            label="Message"
            name="body"
            @blur="$v.body.$touch()"
          />
          <v-btn
            type="submit"
            color="pink"
            class="white--text"
            :disabled=" (body.length<=20)"
            @click="submit"
          >
            SEND MESSAGE
          </v-btn>
          <v-btn @click="clear">
            clear
          </v-btn>
        </form>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, maxLength, email, minLength } from 'vuelidate/lib/validators'
export default {
  metaInfo: {
    title: 'Contact',
    titleTemplate: '%s ← Marcelo Mendonca',
    meta: [
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      {
        name: 'description',
        content:
          "Marcelo Mendonca's Contact Doboj Bosnia and Herzegovina Freelance Get in Touch ContactMe",
      },
      { charset: 'utf-8' },
      { property: 'og:title', content: 'Marcelo Mendonca' },
      { property: 'og:site_name', content: 'Marcelo Mendonca' },
      { property: 'og:type', content: 'website' },
      { property: 'og:url', content: 'https://marcelo-r-mendonca.github.io/' },
      {
        property: 'og:image',
        content: 'https://i.imgur.com/Dcz2PGx.jpg',
      },
      {
        property: 'og:description',
        content:
          "Marcelo Mendonca's Contact Doboj Bosnia and Herzegovina Freelance Get in Touch ContactMe",
      },
    ],
  },
  mixins: [validationMixin],
  validations: {
    name: { required, maxLength: maxLength(20) },
    email: { required, email },
    body: { required, minLength: minLength(20) },
  },
  data() {
    return {
      name: '',
      email: '',
      body: '',
    }
  },
  computed: {
    nameErrors() {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength &&
        errors.push('Name must be at most 20 characters long')
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
    bodyErrors() {
      const errors = []
      if (!this.$v.body.$dirty) return errors
      !this.$v.body.minLength &&
        errors.push('Text must be at least 20 characters long')
      !this.$v.body.required && errors.push('Text is required')
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
      this.body = ''
    },
  },
}
</script>
