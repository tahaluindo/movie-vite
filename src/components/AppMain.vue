<script>

import { store } from "../data/store";
import BaseCard from "./BaseCard.vue";

export default {

    data() {
        return {
            store,
        };
    },

    components: {
        BaseCard
    },

    props: {
        films: Array,
    },

};

</script>

<template>
    <div v-if="store.movieList.length">
        <h2>Films</h2>
        <div class="row row-cols-3">
            <BaseCard v-for="movie in store.movieList" :title="movie.title" :originalTitle="movie.original_title"
                :lang="movie.original_language" :vote="movie.vote_average" />
        </div>
    </div>

    <div v-if="store.TvSeriesList.length">
        <h2>Tv Series</h2>
        <div class="row row-cols-3">
            <BaseCard v-for="TvSeries in store.TvSeriesList" :title="TvSeriesList.name"
                :originalTitle="TvSeries.original_name" :lang="TvSeries.original_language" :vote="TvSeries.vote_average" />
        </div>
    </div>

    <h2 v-if="!store.movieList.length && !store.TvSeriesList.length">Start Searching</h2>
</template>


<style lang="scss" scoped>
ul {
    list-style: none;
}
</style>