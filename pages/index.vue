<template>
  <div>
    <v-container id="hero" style="min-height: 90vh;" fluid>
      <v-row no-gutter class="mt-sm-16 pt-sm-16">
        <v-col>
          <v-row class="text-h4 text-md-h2 mb-3 font-weight-light">
            Hi,
          </v-row>
          <v-row class="text-h4 text-md-h2 mb-3 font-weight-light">
            I'm&nbsp;
            <span class="font-weight-bold pink--text">Marcelo</span>,
          </v-row>
          <v-row class="text-h4 text-md-h2 mb-6 font-weight-light">
            Data Scientist
          </v-row>
          <v-row
            class="text-caption text-sm-subtitle-1 font-weight-light text--lighten-4"
          >
            Data Analytics | Machine Learning | Artificial Intelligence
          </v-row>
        </v-col>
        <v-col class="d-flex justify-center mb-2">
          <img id="hero-image" src="/dashboard.svg" alt="Dashboard" />
        </v-col>
      </v-row>
      <v-row class="justify-center justify-sm-start">
        <v-btn
          class="pink white--text"
          tile
          outlined
          @click="$vuetify.goTo('#about')"
        >
          LEARN MORE
        </v-btn>
      </v-row>
    </v-container>

    <v-divider class="mx-4" inset />
    <v-container id="about" fluid class="mt-16">
      <v-row
        class="pt-4 mb-16 justify-center text-h4 text-md-h3 font-weight-bold"
      >
        About Me
      </v-row>
      <v-row mt-8>
        <v-col class="d-flex justify-center">
          <v-img id="about-avatar" src="/avatar.jpg" alt="Dashboard" />
        </v-col>
        <v-col>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo
            deleniti corporis, consectetur laboriosam doloribus atque expedita
            eaque, esse iure blanditiis nesciunt temporibus quas sint vel
            dolorem illum harum enim non.
          </p>
          <v-btn nuxt to="/resume" class="pink white--text" tile outlined>
            View Resume
          </v-btn>
        </v-col>
      </v-row>
      <!-- <v-row>
        <v-btn nuxt to="/resume" class="pink white--text" tile outlined>
          View Resume
        </v-btn>
      </v-row> -->
    </v-container>

    <!-- Recent Projects -->
    <v-container id="projects" fluid class="mt-16">
      <v-row
        class="pt-4 mb-16 justify-center text-h4 text-md-h3 font-weight-bold"
      >
        Recent Projects
      </v-row>
      <v-row mt-8>
        <ProjectsCards />
        <ProjectsCards />
        <ProjectsCards />
      </v-row>
      <v-row class="mt-8 justify-center">
        <v-btn nuxt to="/portfolio" class="pink white--text" tile outlined>
          View All Projects
        </v-btn>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import ProjectsCards from '~/components/ProjectsCards.vue'

export default {
  components: {
    ProjectsCards,
  },
}
</script>

<style>
#hero-image {
  max-width: 350px;
}
#about-avatar {
  max-width: 250px;
  border-radius: 50%;
}
</style>
