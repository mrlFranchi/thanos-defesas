<template>
  <v-app>
    <ICMCHeader/>
    <v-main>
      <router-view/>
    </v-main>
    <InfoFooter/>
  </v-app>
</template>

<script>
import ICMCHeader from './components/ICMCHeader.vue';
import InfoFooter from './components/InfoFooter.vue';

export default {
  name: 'App',

  data: () => ({
  }),
  components: {
    ICMCHeader,
    InfoFooter,
  },
};
</script>
