<template>
  <div>
    <!-- {{category}} -->
    <!-- {{posts}} -->
  <div class="grid grid-cols-2">
    <nuxt-link class="post-element" :to="`/post/${post.slug}`" v-for="post in posts" :key="post.slug">
      <article class="rounded border-red text-center relative h-full">
        <div class="px-8 flex flex-col flex-1 h-full">
          <div class="flex-1 flex flex-col justify-center">
            <h2 class="PicNic">{{post.title}}</h2>
          </div>
          <div class="flex-1 flex flex-col justify-center">
            <h3>{{post.subheading}}</h3>
          </div>
        </div>
        <img class="rounded box-content border-red lg:absolute post-element-image" :src="post.mainImage.src" :alt="post.mainImage.alt"/>
      </article>
    </nuxt-link>
  </div>
  </div>
</template>

<script>

export default ({
  async asyncData({ $content, params, error }) {
    let category;
    let posts;
    try {
      category = await $content("category", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Project not found" });
    } finally {
      posts = await $content("post").where({ 'category': { $contains: category.title } }).fetch();
    }
    return {
      category,
      posts
    };
  },
})
</script>

<style scoped>
.post-element {
  min-height: 500px;
  max-width: 700px;
}

article:hover .post-element-image {
  transform: translateY(-100%);
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.post-element-image {
  height: 50%;
  bottom: -8px;
  left: -8px;
  width: 100%;
  object-fit: cover;
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}

</style>
