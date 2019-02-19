---
slug: gridsome-post
title: Gridsome
date: 2019-02-18
---

# Gridsome and then some

As part of my learning Vue I thought it would be a good idea to try and rebuild my blog in Vue. There are several static site generators for Vue, the ones I looked at were Nuxt, VuePress, and Gridsome. I chose to use Gridsome because it had GraphQL integration and that was another tool that I wanted to learn about so it became a dual purpose exercise

I started off by installing Gridsome

```
npm i --global @gridsome/cli
```
Take extra care to check that you have all the necessary dependencies installed I kepted running into dependency errors while trying to install and progress through some Gridsome tutorials.

After installation is complete getting the boilerplate ready is as easy as running
```
gridsome create my-project-blog
cd my-project-blog
gridsome develop
```
Gridsome uses pages and layouts in the folder structure. the _Pages_ are the Vue components as well as the routes created for the blog. _pages/Index.vue_ and _pages/About.vue_ create the _/_ and _/about_ routes respectively.

The layouts is a wrapper for the pages to use, as per the [layout docs](https://gridsome.org/docs/layouts/). Gridsome gives you a Default.vue that the pages/Index.vue uses.

Gridsome cannot process markdown. To easily create blog posts we need to add resources to allow for markdown processing and file management. To do this we run the following command to install source-filesystem and transformer-remark
```
npm install --save-dev @gridsome/source-filesystem @gridsome/transformer-remark
```

Then we need to update our gridsome.config.js. Add the following to your module.export
```
transformers: {
    remark: {}
  },
  plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'blog/**/*.md',
        typeName: 'Post',
        route: '/blog/:slug'
      }
    }
  ]
```
By adding these configurations we can create a Post.vue file in templates that will now generate a /blog/ route where the slug in our markdown file will be the route for the post.

Next we create a Post.vue file and add the following to the file:
```
<template>
  <Layout>
    <div v-html="$page.post.content"/>
  </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    content
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
```

Somethings to take note of is the page-query tag in the file. This is source-filesystem. It creates a GraphQL layer for gridsome to access data and fill our posts. We can check the GraphQL queries on our server by looking at [http://localhost:8080/\_\_\_explore](http://localhost:8080/___explore)

Then we can create some blog posts in /blog/ and find these posts by checking /blog/:slug

For more information on creating a Gridsome blog please refer to the references I found below

[https://alligator.io/vuejs/gridsome-blog/](https://alligator.io/vuejs/gridsome-blog/)

[https://alligator.io/vuejs/gridsome-list-posts/](https://alligator.io/vuejs/gridsome-list-posts/)

[https://lobotuerto.com/blog/quickstart-guide-for-a-new-gridsome-project/#add-vuetify-support](https://lobotuerto.com/blog/quickstart-guide-for-a-new-gridsome-project/#add-vuetify-support)
