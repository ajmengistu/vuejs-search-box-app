<template>
  <div class="tmdb-search-item">
    <a
      v-bind:href="'https://www.themoviedb.org/' + result.media_type + '/' + result.id"
      target="_blank"
      rel="noopener noreferrer"
    >
      <img v-bind:src="'https://image.tmdb.org/t/p/h100' + result.poster_path" />
    </a>
    <span>| {{ result.title }} | {{ result.release_date }} | {{ result.vote_average }} ({{ result.vote_count}})</span>
    <!-- <p>{{ result.overview}}</p> -->
  </div>
</template>

<script>
export default {
  name: "TMDBSearchItem",
  props: ["result"],
  methods: {},
};
</script>

<style  scoped>
.tmdb-search-item {
  margin-bottom: 1.2rem;
}

.tmdb-search-item > p {
  text-align: center;
}
</style>