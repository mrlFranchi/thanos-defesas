<template>
  <div>
    <v-app-bar
      color="primary"
      height="110">
      <v-spacer></v-spacer>
      <img
        src="./..\assets\logo.svg"
        width="200"
        height="100"
        alt="Logo do ICMC">
        <v-spacer></v-spacer>
    </v-app-bar>
    <v-app-bar
      height="50">
      <v-tabs
        centered
        class="ml-n9"
        color="grey darken-1"
      >
        <v-tab to="/"
        >
        Home
        </v-tab>
        <v-tab to="/AboutUs"
        >
        About Us
        </v-tab>
      </v-tabs>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data: () => ({
    links: [
      'Home',
      'About',
    ],
  }),
};
</script>
