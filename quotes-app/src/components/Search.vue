<template>
  <div class='bar'>
    <input type='text' placeholder='Search..' v-model='search' />
  </div>
</template>

<script>
// import ListAndPagination from './ListAndPagination.vue'
import data from './json/quotes.json'
export default {
  name: 'Search',
  data() {
      return {
          search: ''
      }
  },
  computed: {
      filteredItems() {
          return data.filter(item => item.quote.includes(this.search))
      }
  }
};
</script>

<style scoped>
    .bar {
        border-radius: 5px;
    }
</style>
