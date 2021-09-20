<template>
  <div>
    <input class="bar" type="text" placeholder="Search by quote" v-model="search" v-on:keyup='updateQuotes()'/>
        <div v-for='item in items' :key='item.id'>
            <div :item='item'>{{ item.quote }}</div>
        <!-- </div> -->
      <!-- <ol class="list">
        <li
          v-for="item in filteredItems"
          :key="item.id"
        >
          <div class="quote">
            "{{ item.quote }}" --{{ item.source }} in
            <div class="character">{{ item.context }}</div>
          </div>
          <br />
          <br />
        </li>
      </ol> -->
    </div>
    <p>Hi</p>
  </div>
</template>

<script>
import data from "./json/quotes.json";
export default {
  name: "Search",
  data() {
    return {
      search: "",
       items: data,
    };
  },
  props: ["visibleItems"],
  methods: {
     updateQuotes() {
      return data.filter(item => item.quote.includes(this.search))
    },
  },
  computed: {
    filteredItems() {
      return data.filter((item) =>
        item.quote.toLowerCase().includes(this.search.toLowerCase())
      );
    },
  },
};
</script>

<style scoped>
.bar {
  border-radius: 5px;
  height: 30px;
}
</style>
