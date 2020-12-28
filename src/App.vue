<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <h1>RunApp</h1>

        
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/elantschner/run-app"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main class="bg">
      <Wettkampfzeiten/>
    </v-main>
  </v-app>
</template>

<script>
import Wettkampfzeiten from './components/Wettkampfzeiten';

export default {
  name: 'App',

  components: {
    Wettkampfzeiten,
  },

  data: () => ({
    //
  }),
};
</script>

<style>
  .bg {
    top: 0;
    left: 0;
    background-image: url(assets/runner.jpg);
    background-size: cover;
  }
</style>
