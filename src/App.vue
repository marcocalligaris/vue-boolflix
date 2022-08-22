<template>
  <div>
    <BaseHeader class="container" @newSearch="search" />
    <main>
      <section id="movies-gallery">
        <h1>MOVIES</h1>
        <MediaCard v-for="movie in movies" :key="movie.id" :media='movie' />
      </section>
      <section id="series-gallery">
        <h1>SERIES</h1>
        <MediaCard v-for="serie in series" :key="serie.id" :media='serie' />
      </section>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import MediaCard from './components/MediaCard.vue';
import BaseHeader from './components/BaseHeader.vue';
export default {
    name: "App",
    components: { MediaCard, BaseHeader },
    data() {
      return {
        movies: [],
        series: [],
        query: "",
        api: {
          baseUri: 'https://api.themoviedb.org/3',
          key: 'b6a442a03c6d2f2cb8e2c9395b576193',
          language: 'it-IT',
        },
      };
    },
    methods: {
        search(query) {
          if(!query) {this.movies = this.series = [];
          return;
          }
          this.getData('/search/movie', query, 'movies');
          this.getData('/search/tv', query, 'series');
        },
        getData(endPoint, query, target) {
          const {baseUri, key, language} = this.api;
          const config = {
            params: {
              api_key: key,
              language,
              query,
            },
          };
          axios.get(`${baseUri}${endPoint}`, config).then((res) => {
            this[target] = res.data.results;
          });
        },
    },
};
</script>

