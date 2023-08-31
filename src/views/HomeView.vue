<template>
  <v-main style="padding: 0;">
  <v-toolbar>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-title>Application</v-toolbar-title>
  </v-toolbar>
  <v-navigation-drawer
    v-model="drawer"
  >
    <!--  -->
  </v-navigation-drawer>
    <!--  -->
  </v-main>
</template>

<script>
export default {
  data: () => ({ drawer: null }),
};
</script>
