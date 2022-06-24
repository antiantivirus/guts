<template>
  <div class="container">
    <!-- {{category}} -->
    <!-- {{posts}} -->
  <Category :category="category.slug"/>
  <div class="category-info lg:mr-8 mx-auto lg:ml-auto mt-6 mb-12 lg:-mt- lg:mb-16 text-center lg:text-left">
    <img src="~assets/img/plaster5.png" class="plaster mx-auto -mb-4" style="transform: rotate(-6deg)"/>
    <div class="rounded border-purple padding">
      <h2 class="mt-6"><nuxt-content :document="category" /></h2>
    </div>
  </div>
  <div class="grid md:grid-cols-2 gap-4 gap-10 lg:gap-16 content-center">
    <nuxt-link class="post-element mx-auto" :to="`/post/${post.slug}`" v-for="post in posts" :key="post.slug">
      <article class="rounded border-red text-center relative h-full">
        <div class="px-8 flex flex-col flex-1 h-full">
          <div class="flex-1 flex flex-col justify-center">
            <h3 class="PicNic h2-picnic">{{post.title}}</h3>
          </div>
          <div class="flex-1 flex flex-col justify-center">
            <h4 class="p">{{post.subheading}}</h4>
          </div>
        </div>
        <Photo :image="post.mainImage" class="rounded box-content border-red absolute post-element-image" />
      </article>
    </nuxt-link>
  </div>
  <div v-if="posts.length == 0" class="rounded border-red padding max-w-prose mx-auto">
    <span class="h2">Ohhhhh....we didn't manage to find anything here. Check back soon :)</span>
  </div>
  </div>
</template>

<script>

export default ({
  head() {
    return {
      title: this.category.title + ' ~ GUTS',
    }
  },
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

.category-info {
  max-width: 500px;
}
</style>
