<template>
  <div>
    <div ref="category" class="absolute mx-auto category-picker z-40 mx-auto" :class="{'fixmeee' : scrolled}">
      <div class="relative">
        <button @click="categoryDropdownOpen = !categoryDropdownOpen" class="rounded small-button block w-full z-50 cursor-s-resize open-category-button capitalize"><span class="mr-2 inline-block" :class="{'im-open':categoryDropdownOpen}" >↓</span>{{category}}</button>
        <transition name="pop-down">
          <div class="w-full text-center absolute top-0 pt-16 pb-2 category-dropdown bg-white z-30" v-show='categoryDropdownOpen'>
            <nuxt-link class="block capitalize" v-for="(category, index) in categories" :key="index" :to="`/explore/${category}`">{{category}}</nuxt-link>
          </div>
        </transition>
      </div>
    </div>
    <img class="mx-auto category-pic mt-36" :src="`/guts/${category}.png`" />
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
      categoryDropdownOpen: false,
      scrolled: null
    }
  },
  props: {
    category: String
  },
  computed: {
    downUp(){
      if (this.categoryDropdownOpen){
        return '↑'
      } else {
        return '↓'
      }
    }
  },
  methods: {
    onScroll(e) {
      // this.scrolled =  /* or: e.target.documentElement.scrollTop */
      if (window.top.scrollY > 120) {
        this.scrolled = true
      } else {
        this.scrolled = false
      }
    }
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll)
  },
  mounted() {
    //remove category that we are on from array
    this.categories.splice(this.categories.indexOf(this.category), 1)
    window.addEventListener("scroll", this.onScroll)
    this.onScroll()
  }
})
</script>

<style>

.category-picker {
  width: 180px;
  left: 50%;
  transform: translateX(-50%);
  top: 145px
}

.fixmeee {
  position: fixed !important;
  top: 25px !important;
}

.im-open {
  transform: rotate(180deg);
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.open-category-button span {
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
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

