<template>

  <header>

    <div class="container-fluid d-flex align-items-center justify-content-between h-100">
        <a class="logo h-100">
            <img class="img-fluid h-100 me-3" src="../assets/img/logo.jpg" alt="Boolflix logo" />
        </a>

        <nav class="navbar navbar-expand-lg me-auto">
           <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" aria-current="page" href="#">Film</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" aria-current="page" href="#">Serie TV</a>
              </li>
            </ul>
        </nav>

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

        li a{
          color: #fff;
          font-size: 1.2rem;

          &:hover{
            color: rgb(187, 58, 58);
          }
        }
    }
</style>