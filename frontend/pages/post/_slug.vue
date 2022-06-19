<template>
  <div class="container">
    <Category :category="post.category[0]"/>
    <!-- {{post}} -->
    <h1 class="text-center max-w-prose mx-auto">{{post.title}}</h1>
    <h2 class="text-center max-w-prose mx-auto">{{post.subheading}}</h2>
    <img class="rounded border-red w-full" :src="post.mainImage.src" :alt="post.mainImage.alt" />
    <div class="w-full rounded border-red large-padding">
      <div class="max-w-prose article-content">
      <nuxt-content :document="post" />
      </div>
    </div>
  </div>
</template>

<script>
  import { groq } from '@nuxtjs/sanity';

  export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("post", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Project not found" });
    } 
    return {
      post
    };
  },
  };
</script>