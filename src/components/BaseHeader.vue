<template>
    <div>
        <BaseSearch placeholder="Cerca qui" @search="fetch" />
    </div>
</template>

<script>
import BaseSearch from './BaseSearch.vue';

export default {
    name: "BaseHeader",
    components: { BaseSearch },
    methods: {
        fetch(query) {
            console.log(query);
        }
    },
}
</script>

