<template>
  <div>
    <h2>Search Wikipedia</h2>
    <SearchBox v-on:search-query="searchWikipedia" />
    <WikipediaSearchList v-bind:wikipediaQueryResults="results" />
  </div>
</template>


<script>
import SearchBox from "../components/common/SearchBox";
import WikipediaSearchList from "../components/wikipedia/WikipediaSearchList";
import axios from "axios";
export default {
  name: "WikipediaSearch",
  components: {
    SearchBox,
    WikipediaSearchList,
  },
  data() {
    return {
      results: [],
    };
  },
  methods: {
    searchWikipedia(searchQuery) {
      axios
        .get(
          `https://en.wikipedia.org/w/api.php?action=query&format=json&origin=*&list=search&srsearch=${searchQuery}`
        )
        .then((response) => {
          this.results = response.data.query.search;
        })
        .catch((error) => console.log(error));
    },
  },
};
</script>