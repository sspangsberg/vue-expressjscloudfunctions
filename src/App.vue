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

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <div v-for="(stuff, index) in info" :key="index">
        {{ stuff.name }}
        {{ stuff.id }}
        {{ stuff.description }}
        {{ stuff.price }}
      </div>
    </v-content>
  </v-app>
</template>

<script>
import axios from 'axios'

export default {
 
  name: 'App',

  components: {
 
  },

  data: () => ({
    info: []
    //
  }),
  mounted () {
    axios
      .get('https://us-central1-expressjs-cloudfunctions-api.cloudfunctions.net/app/api/read')
      .then(response => (this.info = response.data))
      console.log("Testy", this.response)
  },
  watch: {
    
  },
};
</script>
