<template>
    <div>
        <input 
        type="text" 
        v-model.trim="searchTerm"
        @keyup.enter="emitSearch"
        :placeholder="placeholder" 
        />
        <button 
        type="button"
        @click="emitSearch">Cerca</button>
    </div>
</template>

<script>
export default {
    name: 'BaseSearch',
    props: {
        placeholder: String,
    },
    data() {
        return {
            searchTerm: '',
        }
    },
    methods: {
        emitSearch() {
            this.$emit('search', this.searchTerm);
        }
    },
}
</script>

<style></style>
