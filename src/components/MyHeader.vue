<template>
    <SearchComponents @search="searchEmit"/>
</template>

<script>
import SearchComponents from './SearchComponents.vue';

export default {
    name: 'MyHeader',
    components: {
        SearchComponents,
    },
    methods: {
        searchEmit(text) {
            this.$emit("search", text);
        },
    },
}
</script>

<style lang="scss" scoped>

  
</style>