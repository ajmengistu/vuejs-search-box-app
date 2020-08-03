<template>
  <div class="youtube-search-item">
    <a v-bind:href="'https://www.youtube.com/watch?v=' + result.id.videoId">
      <!-- <img v-bind:src="result.thumbnails.default.url" alt /> -->
    </a>
    <span>| {{ result.snippet.title }} | {{ result.snippet.description}}</span>
  </div>
</template>

<script>
export default {
  name: "YouTubeSearchItem",
  props: ["result"],
  method: {},
};
</script>