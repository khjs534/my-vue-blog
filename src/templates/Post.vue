<template>
  <Layout>
    <h1>{{ $page.post.title }} - {{ $page.post.date }}</h1>
    <g-image :alt="$page.post.title" :src="$page.post.image"/>
    <div class="content" v-html="$page.post.content" />
  </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    date (format: "D MMMM, YYYY")
    content
    image (width: 200, height: 200)
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title
    };
  }
};
</script>
