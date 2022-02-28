<template>

  <header>

    <div class="container-fluid d-flex align-items-center justify-content-between h-100">
        <a class="logo h-100">
            <img class="img-fluid h-100" src="../assets/img/logo.jpg" alt="Boolflix logo" />
        </a>
        <SearchComponents @search="emitSearch" />
    </div>

  </header>

</template>

<script>
import SearchComponents from "./SearchComponents.vue";

export default {
  name: "MyHeader",
  components: {
    SearchComponents,
  },
  methods: {
    // lancio evento emit per comunicare con il figlio SearchComponents
    emitSearch(searchText) {
      this.$emit("search", searchText);
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/vars.scss";

    header {
        height: 70px;
        background-color: #000;
        border-bottom: 2px solid red;

        .logo {
            color: $bgColorHeader;
        }
    }
</style>