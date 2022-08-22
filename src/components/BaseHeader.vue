<template>
    <div>
        <BaseSearch placeholder="Cerca qui" @emitSearch="newSearch" />
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


