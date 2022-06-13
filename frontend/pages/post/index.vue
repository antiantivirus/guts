<template>
  <div>
    {{posts}}
    <nuxt-link v-for="post in posts" :to="`post/${post.slug.current}`" :key="post.slug.current">{{post.title}}</nuxt-link>
  </div>
</template>

<script>
  import { groq } from '@nuxtjs/sanity';

  export default {
    computed: {
      category(){
        return this.$route.params.category
      }
    },
    async asyncData({ $sanity, params }) {
      // const query = groq`*[_type == "post"]`;
      const query = groq`*[_type == "post" && $category in categories[]->slug]{
        title,
        slug
      }`
      const posts = await $sanity.fetch(query, { category: params.category });
      return { posts };
    },
  };
</script>
