<template>
  <div>
    <v-app-bar app
      color="primary"
      height="110">
      <v-spacer></v-spacer>
      <img
        src="./..\assets\logo.svg"
        width="200"
        height="100"
        alt="Logo do ICMC">
        <v-spacer></v-spacer>
        <template v-slot:extension>
        <v-tabs centered
          background-color="grey lighten-3"
          color = "grey darken-2">
          <v-tab to="/">Home</v-tab>

          <v-tab to="/aboutus">About</v-tab>
        </v-tabs>
      </template>
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
