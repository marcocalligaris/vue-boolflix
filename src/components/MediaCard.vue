<template>
    <ul>
        <li>{{ media.title || media.name }}</li>
        <li>{{ media.original_title || media.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" :alt="media.original_language">
            <span v-else>{{ media.original_language }}</span>
        </li>
        <li>{{ media.vote_average }}</li>
    </ul>
</template>

<script>
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
    }
},
}
</script>

<style scoped>
    img {
        width: 50px;
    }
</style>