<template>
  <Layout>
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1>Welcome to my Vue Blog</h1>

    <p>
      This is an experiment in rebuilding my blog in Vue with Gridsome.
    </p>
  </Layout>
</template>

<page-query>
query Posts ($page: Int) {
  posts: allPost (perPage: 3, page: $page) @paginate {
    totalCount
    pageInfo {
      totalPages
      currentPage
      isFirst
      isLast
    }
    edges {
      node {
        title
        path
      }
    }
  }
}
</page-query>

<script>
  import { Pager } from "gridsome";

  export default {
    components: {
      Pager
    }
  };
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
