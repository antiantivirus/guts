<template>
  <div>
    <h1>{{post.title}}</h1>
    <SanityContent :blocks="post.content" />
  </div>
</template>

<script>
  import { groq } from '@nuxtjs/sanity';

  export default {
    async asyncData({ params, $sanity }) {
      const query = groq`*[_type == "post" && slug.current == "${params.slug}"][0]`;
      const post = await $sanity.fetch(query);
      return { post };
    },
  };
</script>