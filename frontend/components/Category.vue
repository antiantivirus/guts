<template>
  <div>
    <div class="sticky top-0 category-picker z-40 mx-auto relative mb-6">
      <button @click="categoryDropdownOpen = !categoryDropdownOpen" class="rounded small-button block w-full z-50 cursor-s-resize">{{category}}</button>
      <transition name="pop-down">
        <div class="w-full text-center absolute top-0 pt-16 pb-2 category-dropdown bg-white z-30" v-show='categoryDropdownOpen'>
          <nuxt-link class="block" v-for="(category, index) in categories" :key="index" :to="`/category/${category}`">{{category}}</nuxt-link>
        </div>
      </transition>
    </div>
    <img class="mx-auto category-pic" :src="`/guts/${category}.png`" />
  </div>
</template>

<script>
export default ({
  data(){
    return {
      categories: [
        'music',
        'promo',
        'venue',
        'editorial',
        'budget'
      ],
      categoryDropdownOpen: false
    }
  },
  props: {
    category: String
  },
  mounted() {
    //remove category that we are on from array
    this.categories.splice(this.categories.indexOf(this.category), 1)
  }
})
</script>

<style>

.category-picker {
  width: 180px;
}

.category-dropdown {
  border-radius: 40px;
  background:#D9D9D9;
  z-index: -1;
  border: #000 solid 1px;
}

.category-dropdown a {
  padding: 1rem 0px 1rem 0px;
}

.category-pic {
  max-width: 120px;
}

</style>

