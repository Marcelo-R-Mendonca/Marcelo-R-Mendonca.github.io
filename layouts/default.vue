<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      class="hidden-md-and-up"
      :mini-variant="miniVariant"
      :clipped="clipped"
      temporary
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click.stop="drawer = !drawer"
      />
      <img id="app-bar-avatar" src="/avatar.jpg" alt="Marcelo Mendonca" />

      <v-toolbar-title
        class="pl-3 font-weight-light text-body-2 text-sm-h5"
        v-text="firstName"
      />
      <v-toolbar-title
        class="pl-1 pink--text text-body-2 text-sm-h5"
        v-text="surName"
      />

      <v-spacer />
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn nuxt text to="/" active-class="pink--text headline">
          Home
        </v-btn>
        <v-btn nuxt text to="/resume" active-class="pink--text headline">
          Resume
        </v-btn>
        <!-- <v-btn nuxt text to="/services" active-class="blue--text headline">Services</v-btn> -->
        <v-btn nuxt text to="/portfolio" active-class="pink--text headline">
          Portfolio
        </v-btn>
        <!-- <v-btn nuxt text to="/blog" active-class="blue--text headline">Blog</v-btn> -->
        <v-btn nuxt text to="/contact" active-class="pink--text headline">
          Contact
        </v-btn>
      </v-toolbar-items>
      <v-switch
        v-model="$vuetify.theme.dark"
        class="ml-4"
        hide-details
        flat
        color="pink"
        label="Dark"
      />
    </v-app-bar>

    <v-main>
      <v-container mx-auto class="align-content-center">
        <nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app>
      <span>Marcelo Mendonca &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/',
        },
      ],
      miniVariant: false,
      firstName: 'Marcelo',
      surName: 'Mendonca',
    }
  },
}
</script>

<style>
#app-bar-avatar {
  max-width: 40px;
  border-radius: 50%;
}
</style>
