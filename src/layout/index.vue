<template>
    <v-app id="inspire">
    <v-app-bar
      app
      color="white"
      flat
    >
      <v-container class="py-0 fill-height">
        <v-avatar
          class="mr-10"
          color="grey darken-1"
          size="32"
        ></v-avatar>

        <v-btn
          v-for="link in links"
          :key="link"
          text
        >
          {{ link }}
        </v-btn>

        <v-spacer></v-spacer>

        <v-responsive max-width="260">
          <v-text-field
            dense
            flat
            hide-details
            rounded
            solo-inverted
          ></v-text-field>
        </v-responsive>

        <v-btn text>
          Sign In
        </v-btn>
        <v-btn text>
          Sign Up
        </v-btn>
      </v-container>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <app-main />
    </v-main>
  </v-app>
</template>

<script>
import { AppMain } from './components'
export default {
  name: "Layout",
  components: {
     AppMain 
  },
  data: () => ({
    //
  }),
};
</script>