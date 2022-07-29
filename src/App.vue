<template>
  <div>
    <BaseSearch placeholder="Cerca qui" @search="fetch"/>
    <section id="movies">
      <h1>MOVIES</h1>
      <ul v-for="movie in movies" :key="movie.id">
        <li>{{movie.title}}</li>
        <li>{{movie.original_title}}</li>
        <li>{{movie.original_language}}</li>
        <li>{{movie.vote_average}}</li>
      </ul>
    </section>
  </div>
</template>

<script>
import BaseSearch from './components/BaseSearch.vue';
import axios from 'axios';
export default {
    name: "App",
    components: { BaseSearch },
    data() {
      return {
        movies: [],
        api: {
          baseUri: 'https://api.themoviedb.org/3',
          key: 'b6a442a03c6d2f2cb8e2c9395b576193',
          language: 'it-IT',
        },
      };
    },
    methods: {
        fetch(query) {
          const {baseUri, key, language} = this.api;
          const config = {
            params: {
              api_key: key,
              language,
              query,
            },
          };
          axios.get(baseUri + '/search/movie', config).then((res) => {
            this.movies = res.data.results
          })
        },
    },
}
</script>
