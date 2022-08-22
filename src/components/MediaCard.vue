<template>
<div id="media-card">
    <img id="media-poster" class="w-100" :src="posterCover" :alt="media.title">
    <ul class="p-0">
        <li>Titolo: {{ media.title || media.name }}</li>
        <li>Titolo originale: {{ media.original_title || media.original_name }}</li>
        <li>Voto: 
            <i 
            v-for="x in 5" 
            :key="x" 
            class="fa-star" 
            :class="mediaVote >= x ? 'fa-solid': 'fa-regular'" 
            ></i
            ></li>
        <li>
            <img id="flag" v-if="hasFlag" :src="flagSrc" :alt="media.original_language">
            <span v-else>{{ media.original_language }}</span>
        </li>
    </ul>
</div>
</template>

<script>
const coverPlaceholder = 'https://critics.io/img/movies/poster-placeholder.png';
export default {
name: 'MediaCard',
props: {
    media: Object,
},
computed: {
    hasFlag() {
        const flags = ['it', 'en'];
        return flags.includes(this.media.original_language);
    },
    flagSrc() {
        return require(`../assets/img/flags/${this.media.original_language}.png`);
    },
    mediaVote() {
        return Math.ceil(this.media.vote_average / 2);
    },
    posterCover() {
        if (!this.media.poster_path) return coverPlaceholder;
        return 'https://image.tmdb.org/t/p/w342' + this.media.poster_path;
    },
},
}
</script>

<style lang="scss" scoped>
#media-poster {
    cursor: pointer;
    display: block;
};
ul {
    cursor: pointer;
    list-style-type: none;
    display: none;
  li {
      margin-bottom: 10px;
    font-weight: bold;
  }
  #flag {
      height: 30px;
  }
};
#media-card #media-poster, #media-card:hover #media-poster{
    display: none;
};
#media-card ul, #media-card:hover ul{
    display: block;
};


</style>
