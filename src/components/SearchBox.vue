<template>
  <div class="container">
    <div class="input-group mb-3">
      <input
        @input="onChange"
        v-model="searchQuery"
        type="text"
        class="form-control"
        aria-label="Sizing example input"
        aria-describedby="inputGroup-sizing-default"
        placeholder="Search for movie, show, & cast..."
      />
    </div>
    <div>
        <div ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeachBox",
  data() {
    return {
      searchQuery: "",
    };
  },
  methods: {
    onChange() {
    //   console.log(this.searchQuery);
      // send up the parent
        this.$emit("search-query", this.searchQuery);
    },
  },
};
</script>

<style lang="stylus" scoped></style>