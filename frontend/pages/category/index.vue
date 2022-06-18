<template>
  <div class="h-100">
    {{hovering}}
    <!-- {{categories}} -->
    <div id="promo" class="gut-element lg:absolute" @mouseenter="hovering = 'promo'" @mouseleave="hovering = null">
      <div class="relative w-full h-full">
        <nuxt-link to="/category/promo"><img class="drop-shadow-png" src="~assets/img/guts/Brain-900.png" alt="Promo" /></nuxt-link>
        <div class="lg:hidden lg:absolute info" :class="{'lg:block' : hovering == 'promo'}">
          <h2>{{promo[0].title}}</h2>
          {{promo[0].body}}
        </div>
      </div>
    </div>

    <div id="venue" class="gut-element lg:absolute" @mouseenter="hovering = venue" @mouseleave="hovering = null">
      <nuxt-link  to="/category/venue"><img class="drop-shadow-png" src="~assets/img/guts/House-900.png" alt="Venue" /></nuxt-link>
      <div>
        <h2>{{promo.title}}</h2>
      </div>
    </div>

    <div id="music" class="gut-element lg:absolute" @mouseenter="hovering = music" @mouseleave="hovering = null">
      <nuxt-link  to="/category/music"><img class="drop-shadow-png" src="~assets/img/guts/Music-Note-900.png" alt="Music" /></nuxt-link>
      <div>
        <h2>{{promo.title}}</h2>
      </div>
    </div>

    <div id="editorial" class="gut-element lg:absolute" @mouseenter="hovering = editorial" @mouseleave="hovering = null">
      <nuxt-link  to="/category/editorial"><img class="drop-shadow-png" src="~assets/img/guts/Pencil-900.png" alt="Editorial" /></nuxt-link>
      <div>
        <h2>{{promo.title}}</h2>
      </div>
    </div>

    <div id="budget" class="gut-element lg:absolute" @mouseenter="hovering = budget" @mouseleave="hovering = null">
      <nuxt-link  to="/category/budget"><img class="drop-shadow-png" src="~assets/img/guts/Pound-900.png" alt="Budget" /></nuxt-link>
      <div>
        <h2>{{promo.title}}</h2>
      </div>
    </div>
  </div>
</template>


<script>

export default ({
  data(){
    return {
      hovering: null
    }
  },
  async asyncData({ $content }) {
    // const categories = await $content("category").fetch()
    const promo = await $content("category").where({ slug: 'promo' }).fetch()
    const venue = await $content("category").where({ slug: 'venue' }).fetch()
    const music = await $content("category").where({ slug: 'music' }).fetch()
    const editorial = await $content("category").where({ slug: 'editorial' }).fetch()
    const budget = await $content("category").where({ slug: 'budget' }).fetch()
    return {
      // categories,
      promo,
      venue,
      music,
      editorial,
      budget
    };
  },
})
</script>


<style scoped>
.gut-element:hover {

}

/* 'lg': '1024px', */
@media (min-width: 1024px) {
  .gut-element {
    min-width: 240px;
    min-height: 240px;
    width: 15vw;
    height: 15vw;
    padding: 2rem;
  }

  .gut-info {
    bottom: 0%;
    right: 0%;
  }

  #promo {
    top: 10%;
    left: 10%
  }


  #venue {
    bottom: 10%;
    left: 25%;
  }

  #music {
    top: 20%;
    left: 38%
  }

  #editorial {
    bottom: 12%;
    right: 20%;
    width: 22vw;
  }

  #budget {
    top: 10%;
    right: 10%;
  }
}
</style>
