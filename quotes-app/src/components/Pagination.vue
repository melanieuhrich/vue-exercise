<template>
  <section>
    <!-- <b-pagination
            :total="total"
            v-model="current"
            :range-before="rangeBefore"
            :range-after="rangeAfter"
            :order="order"
            :size="size"
            :simple="isSimple"
            :rounded="isRounded"
            :per-page="perPage"
            :icon-prev="prevIcon"
            :icon-next="nextIcon"
            aria-next-label="Next page"
            aria-previous-label="Previous page"
            aria-page-label="Page"
            aria-current-label="Current page">
        </b-pagination>
    <h2>Hello</h2>
    <h1>Hi</h1> -->
    <div class="pagination">
      <a href="#">&laquo;</a>
      <a href="#">1</a>
      <a class="active" href="#">2</a>
      <a href="#">3</a>
      <a href="#">4</a>
      <a href="#">5</a>
      <a href="#">6</a>
      <a href="#">&raquo;</a>
    </div>
  </section>
</template>

<script>
export default {
  name: "Pagination",
};
</script>

<style scoped>
    /* Pagination links */
    .pagination a {
        color: black;
        float: left;
        padding: 8px 16px;
        text-decoration: none;
        transition: background-color 0.3s;
    }
    /* Style the active/current link */
    .pagination a.active {
        background-color: dodgerblue;
        color: white;
    }
    /* Add a grey background color on mouse-over */
    .pagination a:hover:not(.active) {
        background-color: #ddd;
    }
    .pagination {
        margin-left: 300px;
        margin-right: 300px
    }
</style>