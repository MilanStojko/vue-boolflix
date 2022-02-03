<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      filmsArray: [],
      tvsArray: [],
    };
  },
  props: {},
  methods: {
    research() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "4ebf036aac28ea5ef76675bc26c8db26",
            query: this.inputresearch,
          },
        })
        .then((response) => {
          this.filmsArray = response.data.results;
          console.log("Risposta GET tvs");
          axios
            .get("https://api.themoviedb.org/3/search/tv", {
              params: {
                api_key: "4ebf036aac28ea5ef76675bc26c8db26",
                query: this.inputresearch,
              },
            })
            .then((response) => {
              this.tvsArray = response.data.results;
              console.log("Risposta GET tvs");
            });
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
</style>
