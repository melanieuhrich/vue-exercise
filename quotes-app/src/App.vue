<template>
  <section>
    <Heading />
    <Search class='top' />
    <Filter class='top' />
    <ListAndPagination />
  </section>
</template>

<script>
import Heading from "./components/Heading.vue";
import ListAndPagination from "./components/ListAndPagination.vue";
import Filter from "./components/Filter.vue";
import Search from "./components/Search.vue";

export default {
  name: "App",
  components: {
    Heading,
    ListAndPagination,
    Filter,
    Search
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.top {
  display: inline
}
</style>
