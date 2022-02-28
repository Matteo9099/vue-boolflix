<template>

  <section v-if="items.length > 0" :id="id" class="my-5">
    <div class="title-container">
        <h2 class="h1 text-center">{{ title }}</h2>
    </div>

    <div class="card-container d-flex flex-wrap justify-content-center">
        <CardComponent v-for="item in items" :key="item.id" :item="item" />
    </div>
  </section>

</template>

<script>
import CardComponent from "./CardComponent.vue";

export default {
  name: "ResultComponents",
  components: { CardComponent },
  props: ["id", "title", "items"],
};
</script>

<style scoped lang="scss">

    .title-container {
        position: relative;
        color: red;

        h2 {
            font-family: sans-serif;
            font-weight: bold;
            font-size: 50px;
        }
    }

</style>