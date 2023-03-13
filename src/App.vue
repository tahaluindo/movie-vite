<script>

// IMPORT DEL COMPONENTE
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from "./data/store"

import axios from "axios"

// DEFINIZIONE DEL COMPONENTE IN PAGINA
export default {

  data() {
    return {
      store
    };
  },

  components: {
    AppHeader, AppMain
  },

  methods: {

    fetchResults(term) {
      this.fetchMovies(term);
      this.fetchTvSeries(term);
    },

    fetchMovies(query) {
      axios
        .get(
          `${store.BaseURI}/search/movie`, {
          params: {
            api_key: store.apiKey,
            query,
          }
        }
        )
        .then((response) => {
          store.movieList = response.data.results;
          console.log(store.movieList);
        })
    },

    fetchTvSeries(query) {
      axios
        .get(
          `${store.BaseURI}/search/tv`, {
          params: {
            api_key: store.apiKey,
            query,
          }
        }
        )
        .then((response) => {
          store.TvSeriesList = response.data.results;
          console.log(store.TvSeriesList);
        })
    }
  }
};

</script>

<template>
  <AppHeader @performSearch="fetchResults" />

  <div class="container my-5">
    <AppMain :films="store.movieList" />
  </div>
</template>


<style lang="scss"></style>