<template>
  <section>
    <img alt="Vue logo" src="./assets/logo.png" />
    <Heading />
    <QuotesList />
    <Pagination />
    <Filter />
  </section>
</template>

<script>
import Heading from "./components/Heading.vue";
import QuotesList from "./components/QuotesList.vue";
import Pagination from "./components/Pagination.vue";
import Filter from "./components/Filter.vue";

export default {
  name: "App",
  components: {
    Heading,
    QuotesList,
    Pagination,
    Filter,
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
</style>
