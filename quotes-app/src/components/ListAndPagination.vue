<template>
  <section>
    <input
      class="bar top"
      type="text"
      placeholder="Search by quote..."
      v-model="search"
      v-on:keyup="updateQuotes()"
      v-on:keyup.delete="updateVisibleItems()"
    />
    <button id='m' type="button" class="filter-btn top" @click='getMovieQuotes()'>Movie Quotes</button>
    <button id='games' type="button" class="filter-btn top" @click="getGameQuotes()">Game Quotes</button>
    <button type="button" class="filter-btn top" @click="updateVisibleItems()">All Quotes</button>
    <div>
      <ul class="list">
        <li
          v-for="item in visibleItems"
          v-bind:visibleItems="visibleItems"
          v-bind:currentPage="currentPage"
          :key="item.id"
        >
          <div class="quote">
            "{{ item.quote }}" --{{ item.source }} in
            <div class="character">{{ item.context }}</div>
          </div>
          <br />
          <br />
        </li>
      </ul>
      <div v-if="totalPages()" class="pagination-wrapper">
        <button
          v-if="showPreviousLink()"
          class="pagination-btn"
          v-on:click="updatePage(currentPage - 1)"
        >
          Previous
        </button>
        <button
          v-if="showNextLink()"
          class="pagination-btn"
          v-on:click="updatePage(currentPage + 1)"
        >
          Next
        </button>
        <div>Page {{ currentPage + 1 }} of {{ totalPages() }}</div>
      </div>
    </div>
  </section>
</template>

<script>
import data from "./json/quotes.json";

export default {
  name: "ListAndPagination",
  data() {
    return {
      items: data,
      currentPage: 0,
      pageSize: 10,
      visibleItems: [],
      search: "",
    };
  },
  beforeMount: function () {
    this.updateVisibleItems();
  },
  methods: {
    updateQuotes() {
      this.visibleItems = this.items.filter((item) =>
        item.quote.includes(this.search)
      );
    },
    getMovieQuotes() {
      this.visibleItems = this.items.filter((item) => item.theme === 'movies')
    },
     getGameQuotes() {
      this.visibleItems = this.items.filter((item) => item.theme === 'games')
    },
    updatePage(pageNumber) {
      this.currentPage = pageNumber;
      this.updateVisibleItems();
    },
    updateVisibleItems() {
      this.visibleItems = this.items.slice(
        this.currentPage * this.pageSize,
        this.currentPage * this.pageSize + this.pageSize
      );
      //If we have 0 visible items, we go back a page
      if (this.visibleItems.length == 0 && this.currentPage > 0) {
        this.updatePage(this.currentPage - 1);
      }
    },
    totalPages() {
      return Math.ceil(this.items.length / this.pageSize);
    },
    showPreviousLink() {
      return this.currentPage == 0 ? false : true;
    },
    showNextLink() {
      return this.currentPage == this.totalPages() - 1 ? false : true;
    },
  },
};
</script>

<style scoped>
.bar {
  border-radius: 5px;
  height: 30px;
  margin: 5px;
}
.top {
  display: inline;
}
.filter-btn {
  margin: 5px;
  height: 35px;
  background-color: lightblue;
  border-radius: 5px;
}
.list {
  margin-top: 50px;
  margin-bottom: 50px;
  margin-left: 100px;
  margin-right: 100px;
  text-align: left;
}
.quote {
  display: inline;
}
.character {
  display: inline;
  font-style: italic;
}
.pagination {
  margin-left: 300px;
  margin-right: 300px;
}
.pagination-btn {
  cursor: pointer;
  height: 35px;
  margin: 5px;
  background-color: lightblue;
  border-radius: 5px;
}
</style>
