<template>
  <v-app>
    <v-app-bar app>
      <!-- <v-toolbar-title class="headline text-uppercase">
        <span>Bar</span>
        <span class="font-weight-light">KARTE</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>-->
      <v-tabs right>
        <v-tab @click="category = ''" text>Alle</v-tab>
        <v-tab @click="category = 'classic'" text>Klassiker</v-tab>
        <v-tab @click="category = 'gin'" text>Gin</v-tab>
        <v-tab @click="category = 'wodka'" text>Wodka</v-tab>
        <v-tab @click="category = 'pitu'" text>Cachaça</v-tab>
        <v-tab @click="category = 'aperol'" text>Aperol</v-tab>
        <v-tab @click="category = 'alcoholFree'" text>Alkoholfrei</v-tab>
      </v-tabs>
    </v-app-bar>
    <v-content app>
      <Cocktails :category="category" />
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import Cocktails from "./components/Cocktails.vue";

export default Vue.extend({
  name: "App",
  components: {
    Cocktails,
  },
  data: () => ({
    category: "",
  }),
});
</script>
<style lang="scss">
* {
  border-radius: 0 !important;
}

html {
  overflow: scroll;
  overflow-x: hidden;
}

::-webkit-scrollbar {
  width: 0px;
  /* Remove scrollbar space */
  background: transparent;
  /* Optional: just make scrollbar invisible */
}

/* Optional: show position indicator in red */
::-webkit-scrollbar-thumb {
  background: #ff0000;
}
</style>
