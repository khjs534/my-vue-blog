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
