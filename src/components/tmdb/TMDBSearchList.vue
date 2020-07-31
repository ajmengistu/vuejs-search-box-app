<template>
  <div>
    <h3>The Movie DB</h3>
    <div v-bind:key="result.id" v-for="result in queryResults">
      <TMDBSearchItem v-bind:result="result" />
    </div>
  </div>
</template>

<script>
import TMDBSearchItem from "./TMDBSearchITem";

export default {
  name: "TMDBSearchList",
  components: {
    TMDBSearchItem,
  },
  props: ["queryResults"],
};
</script>

<style  scoped>
h3 {
  text-decoration: underline;
  margin-bottom: 1rem;
}
</style>