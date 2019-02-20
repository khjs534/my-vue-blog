<template>
  <Layout>
    <p v-for="post in $page.posts.edges">
      <g-link :to="post.node.path">
        {{ post.node.title }}
      </g-link>
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

</script>
