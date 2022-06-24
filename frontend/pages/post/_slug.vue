<template>
  <div class="container">
    <Category :category="post.category[0]"/>
    <!-- {{post}} -->
    <h1 class="text-center max-w-prose mx-auto mb-4 lg:mb-6">{{post.title}}</h1>
    <h2 class="text-center max-w-prose mx-auto mb-6 lg:mb-12">{{post.subheading}}</h2>
    <img src="~assets/img/plaster5.png" class="plaster mx-auto -mb-4 lg:-mb-8 z-10" style="transform: rotate(-8deg)"/>
    <img class="rounded border-red w-full" :src="post.mainImage.src" :alt="post.mainImage.alt" />
    <img src="~assets/img/plaster5.png" class="plaster mx-auto -mb-3 -mt-3" style="transform: rotate(8deg)"/>
    <div class="w-full rounded border-red large-padding">
      <div class="max-w-prose article-content">
      <nuxt-content class="mt-6" :document="post" />
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    head() {
      return {
        title: this.post.title + '~ GUTS',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: this.post.subheading
          },
          {
            hid: 'og:image',
            property: 'og:image',
            content: this.post.mainImage.src
          }
        ]
      }
    },
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