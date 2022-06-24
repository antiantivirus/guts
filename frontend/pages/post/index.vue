<template>
  <div>
    {{posts}}
    <nuxt-link v-for="post in posts" :to="`post/${post.slug.current}`" :key="post.slug.current">{{post.title}}</nuxt-link>
  </div>
</template>

<script>
</script>
