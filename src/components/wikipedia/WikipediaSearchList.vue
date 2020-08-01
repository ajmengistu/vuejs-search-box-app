<template>
  <div>
    <h3>Wikipedia</h3>
    <div v-bind:key="result.pageid" v-for="result in wikipediaQueryResults">
      <WikipediaSearchItem v-bind:result="result" />
    </div>
  </div>
</template>

<script>
import WikipediaSearchItem from "./WikipediaSearchItem";
export default {
  name: "WikipediaSearchList",
  components: {
    WikipediaSearchItem,
  },
  props: ["wikipediaQueryResults"],
};
</script>


<style  scoped>
</style>