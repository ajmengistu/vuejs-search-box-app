<template>
  <div>
    <h3>YouTube</h3>
    <div v-bind:key="result.id.videoId" v-for="result in youtubeQueryResults">
      <YouTubeSearchItem v-bind:result="result" />
    </div>
  </div>
</template>

<script>
import YouTubeSearchItem from "./YouTubeSearchItem";

export default {
  name: "YouTubeSearchList",
  components: {
    YouTubeSearchItem,
  },
  props: ["youtubeQueryResults"],
};
</script>

<style>
h3 {
  text-decoration: underline;
  margin-bottom: 1rem;
}
</style>