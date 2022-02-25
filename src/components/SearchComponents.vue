<template>
    <section class="container-fluid d-flex justify-content-between align-items-center">
        <div class="logo">
            <h2>Boolflix</h2>
        </div>
        <div class="p-3 mx-5 d-flex align-items-center">

            <input type="text" placeholder="Cerca Film o Serie Tv..." class="px-5 me-3" v-model.trim="searchFilm" @keyup="searchEmit">

            <button class="btn btn-danger" @click="searchEmit">Cerca</button>

        </div>
    </section>
</template>

<script>
export default {
    name: 'SearchComponents',
    data() {
        return {
            searchFilm: '',
        };
    },
    methods: {
        searchEmit() {
            this.$emit("search", this.searchFilm);
        },
     },
};
</script>


<style lang="scss" scoped>
    @import '../assets/style/vars.scss';

    section{
        background-color: $bgColorHeader;
    }


</style>