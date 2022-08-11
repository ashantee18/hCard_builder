<template>
  <v-app>
    <v-main class="grey lighten-3">
      <v-container class="grey lighten-5 my-6" fluid>
      <CardForm/>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import CardForm from "./components/CardForm";

export default {
  name: "App",

  components: {
    CardForm,
  },

   data () {},
};
</script>
<style>
@import './assets/styles/index.css';
</style>