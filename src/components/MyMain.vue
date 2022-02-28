<template>
  <main>
    <div class="container my-3">
      <ResultComponents id="movies" title="Film" :items="movies" />
      <ResultComponents id="series" title="Serie TV" :items="series" />
      <p class="startTitle h1 text-center" 
        v-if="(movies.length && series.length) === 0">
        Cerca un Film o una Serie TV!
      </p>
    </div>
  </main>
</template>

<script>
import ResultComponents from "./ResultComponents.vue";

export default {
  name: "MyMain",
  components: { ResultComponents },
  props: {
    'movies': Array,
    'series': Array
  },
};
</script>

<style scoped lang="scss">

    .startTitle {
        font-family: "fantasy";
        color: red;
        font-weight: bold;
        padding-top: 50px;
    }

</style>