<template>
  <div id="app">
    <SearchBox v-on:search-query="searchTMDB" />
    <TMDBSearchList v-bind:queryResults="queryResults" />
  </div>
</template>

<script>
import SearchBox from "../components/SearchBox";
import TMDBSearchList from "../components/TMDBSearchList";
import axios from "axios";

export default {
  name: "Home",
  components: {
    SearchBox,
    TMDBSearchList,
  },
  data() {
    return {
      queryResults: [],
    };
  },
  methods: {
    searchTMDB(searchQuery) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/multi?api_key=1a7eb2f78daf0c6f300f6b339f4f5030&language=en-US&query=${searchQuery}&page=1&include_adult=false`
        )
        .then((response) => {
          this.queryResults = response.data.results;
          this.queryResults = this.queryResults.slice(0, 5);
        })
        .catch((error) => console.log(error));
    },
  },
};
</script>
