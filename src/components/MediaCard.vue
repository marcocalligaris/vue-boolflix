<template>
    <ul>
        <li>{{ media.title || media.name }}</li>
        <li>{{ media.original_title || media.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" :alt="media.original_language">
            <span v-else>{{ media.original_language }}</span>
        </li>
        <li>
            <i 
            v-for="x in 5" 
            :key="x" 
            class="fa-star" 
            :class="mediaVote >= x ? 'fa-solid': 'fa-regular'" 
            ></i
            > {{ mediaVote }}
            </li>
        <li><img :src="posterCover" :alt="title"></li>
    </ul>
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
    }
},
}
</script>

<style scoped>

</style>
