<template>
    <div class="py-4" id="header">
        <div class="container d-flex justify-content-between align-items-center">
            <a href="#"><h1>BOOLFLIX</h1></a>
            <BaseSearch placeholder="Cerca qui" @search="newSearch" />
        </div>
    </div>
</template>

<script> 
import BaseSearch from './BaseSearch.vue';

export default {
    name: "BaseHeader",
    components: { BaseSearch },
    methods: {
        newSearch(value) {
            this.$emit('search', value);
        },
    },
}
</script>
<style lang="scss" scoped>
#header {
    background-color: black;
    position: sticky;
    left: 0;
    right: 0;
    top: 0;
    a {
        text-decoration: none;
        color: red;
        font-size: 1.5rem;
    }
}
</style>


