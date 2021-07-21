<template>
  <v-app id="inspire">
    <v-app-bar app color="white" flat>
      <v-row align="center" justify="space-around">
        <v-container class="py-0 fill-height">
          <v-avatar size="50">
            <v-img :src="img"></v-img>
          </v-avatar>

          <h1 class="blue--text text--darken-4">VSTECS</h1>
          <v-spacer />
          <v-col v-for="link in links" :key="link">
            <v-btn
              @click="clickmenu(link)"
              depressed
              block
              color="blue-grey"
              dark
              x-large
            >
              {{ link }}
            </v-btn>
          </v-col>
          <v-spacer></v-spacer>
          {{ user.name }}
        </v-container>
      </v-row>
    </v-app-bar>

    <v-main  >
      <router-view />
    </v-main>
    <v-footer app color="blue-grey" class="white--text">
      <span>VST ECS (Thailand) Co.,Ltd.</span>
      <v-spacer />
      <span>&copy; 2021 (version 0.0.3)</span>
    </v-footer>
  </v-app>
</template>

<script>
import { msalMixin } from "vue-msal";
 
export default {
  mixins: [msalMixin],
  data: () => ({
    img: process.env.VUE_APP_REDIRECT + "/vstecs.png",
    links: ["Dashboard", "Query"],
  }),
  methods: {
    async clickmenu(item) {
       /*
      if (item != this.$route.name) {
        this.$router.push({ name: item }).go;
      }*/
    },
  },
  computed: {
    user() {
      let user = {};
      if (this.msal.isAuthenticated) {
        this.msal.graph.callAfterInit = true;
        
        user = {
          ...this.msal.user,
          profile: {},
        };
        if (this.msal.graph && this.msal.graph.profile) {
          user.profile = this.msal.graph.profile;
        }
      } else {
        this.$msal.signIn();
      }
      return user;
    },
  },
};
</script>