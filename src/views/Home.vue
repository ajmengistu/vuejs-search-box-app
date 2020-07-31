<template>
  <div id="app">
    <SearchBox v-on:search-query="updateSearchQuery" />
    <TMDBSearchList v-bind:queryResults="queryResults" />
    <YouTubeSearchList v-bind:youtubeQueryResults="youtubeQueryResults" />
  </div>
</template>

<script>
import SearchBox from "../components/common/SearchBox";
import TMDBSearchList from "../components/tmdb/TMDBSearchList";
import YouTubeSearchList from "../components/youtube/YouTubeSearchList";
import axios from "axios";

export default {
  name: "Home",
  components: {
    SearchBox,
    TMDBSearchList,
    YouTubeSearchList,
  },
  data() {
    return {
      queryResults: [],
      youtubeQueryResults: [],
    };
  },
  methods: {
    updateSearchQuery(searchQuery) {
      this.searchTMDB(searchQuery);
      this.searchYouTube(searchQuery);
    },
    searchTMDB(searchQuery) {
      this.queryResults = [...this.queryResults, searchQuery];
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
    searchYouTube(searchQuery) {
      axios
        .get(
          `https://www.googleapis.com/youtube/v3/search?part=snippet&maxResults=5&q=${searchQuery}&key=AIzaSyDEo3Pw-0ZZ_F4sPWadom9CE1ISNQKivy0`
        )
        .then((response) => {
          this.youtubeQueryResults = response.data.items;
        })
        .catch((error) => console.log(error));
    },
  },
};
</script>
