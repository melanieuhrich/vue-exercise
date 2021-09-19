<template>
  <section>
    <ol class='list'>
      <li
        v-for="item in visibleItems"
        v-bind:visibleItems="visibleItems"
        v-bind:currentPage="currentPage"
        :key="item.id"
      >
        <div class="quote">
          "{{ item.quote }}" -- {{ item.source }} in
          <div class="character">{{ item.context }}</div>
        </div>
        <br />
        <br />
      </li>
    </ol>
    <div v-if="totalPages()" class="pagination-wrapper">
      <button
        v-if="showPreviousLink()"
        class="pagination-btn"
        v-on:click="updatePage(currentPage - 1)"
      >
        Previous
      </button>
      <!-- {{ currentPage + 1 }} of {{ totalPages() }} -->
      <button
        v-if="showNextLink()"
        class="pagination-btn"
        v-on:click="updatePage(currentPage + 1)"
      >
        Next
      </button>
      <div>Page {{ currentPage + 1 }} of {{ totalPages() }}</div>
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
    };
  },
  beforeMount: function () {
    this.updateVisibleItems();
  },
  methods: {
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
    // updatePage(pageNumber) {
    //   this.$emit("page:update", pageNumber);
    // },
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
