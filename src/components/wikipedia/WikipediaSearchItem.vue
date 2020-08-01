<template>
  <div>
    <a v-bind:href="'https://wikipedia.com/wiki/' + result.title" target="_blank">
      <h5>{{result.title}}</h5>
    </a>
    <div v-html="result.snippet"></div>
  </div>
</template>


<script>
export default {
  name: "WikipediaSearchItem",
  props: ["result"],
  method: {},
};
</script>

<style scoped>
</style>