<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Jared Stevens Tech Exam</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-avatar tile height="30" width="90">
        <img :src="image" />
      </v-avatar>
    </v-app-bar>
    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      image: require("@/assets/zoovu-logo.png")
    };
  }
};
</script>
