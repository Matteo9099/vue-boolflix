<template>
  <!-- Creazione input con button -->
  <div class="search-container d-flex align-items-center">
    <!-- l'input al rilascio del tasto "enter" richiama il metodo che segue -->
    <input
      @keyup.enter="emitSearch"
      v-model.trim="searchText"
      placeholder="Cerca un film o una serie tv"
      type="text"
      class="search-input px-4 py-2 me-3"
    />
    <!-- il bottone al click richiama il metodo che segue  -->
    <button @click.prevent="emitSearch" class="btn btn-danger px-3">Cerca</button>
  </div>

</template>

<script>
export default {
  name: "SearchComponents",   
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    // lancio evento emit per comunicare con il genitore MyHeader
    emitSearch() {
        this.$emit("search", this.searchText);
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/vars.scss";

    .search-input {
        width: 300px;
        border: 0;
        background-color: $bgColorHeader;
        color: rgb(180, 176, 176);
        padding-left: 5px;
        border-radius: 5px;
    }

    button {
        border: 0;
        color: #fff;
        border-radius: 5px;
    }

</style>