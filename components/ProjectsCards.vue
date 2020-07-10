<template>
  <v-card class="mx-auto my-2" max-width="300">
    <v-img src="/bar_chart.svg" height="150px" alt="Bar Chart" />

    <v-card-title>
      Project Name
    </v-card-title>

    <v-card-subtitle>
      Technology used
    </v-card-subtitle>

    <v-card-actions>
      <v-btn text>
        Learn More
      </v-btn>

      <v-btn color="pink" text>
        Live Demo
      </v-btn>

      <v-spacer />

      <v-btn icon @click="show = !show">
        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider />

        <v-card-text>
          I'm a thing. But, like most politicians, he promised more than he
          could deliver. You won't have time for sleeping, soldier, not with all
          the bed making you'll be doing. Then we'll go with that data file!
          Hey, you add a one and two zeros to that or we walk! You're going to
          do his laundry? I've got to find a way to escape.
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    show: false,
  }),
}
</script>
