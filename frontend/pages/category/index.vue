<template>
  <div class="lg:h-screen container">
    <div id="promo" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'promo'" @mouseleave="hovering = null">
      <nuxt-link to="/category/promo">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/promo.png" alt="Promo" />
        <transition name="pop-down">
          <div class="relative gut-info rounded border-purple padding" v-show="hovering == 'promo'">
            <h2 class="mb-3 mt-1">{{promo[0].title}}</h2>
            <nuxt-content :document="promo[0]" />
          </div>
        </transition>
        <div class="rounded border-purple padding lg:hidden max-w-prose mx-auto -mt-16">
            <h2 class="mb-3 mt-1">{{promo[0].title}}</h2>
            <nuxt-content :document="promo[0]" />
        </div>
      </nuxt-link>
    </div>

    <div id="venue" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'venue'" @mouseleave="hovering = null">
      <nuxt-link class="z-50" to="/category/venue">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/venue.png" alt="Venue" />
        <transition name="pop-down">
          <div id="venue-info" class="relative gut-info rounded border-purple padding" v-show="hovering == 'venue'">
            <h2 class="mb-3 mt-1">{{venue[0].title}}</h2>
            <nuxt-content :document="venue[0]" />
          </div>
        </transition>
        <div class="rounded border-purple padding lg:hidden max-w-prose mx-auto -mt-16">
            <h2 class="mb-3 mt-1">{{venue[0].title}}</h2>
            <nuxt-content :document="venue[0]" />
        </div>
      </nuxt-link>
    </div>

    <div id="music" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'music'" @mouseleave="hovering = null">
      <nuxt-link  to="/category/music">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/music.png" alt="Music" />
        <transition name="pop-down">
          <div class="relative gut-info rounded border-purple padding" v-show="hovering == 'music'">
            <h2 class="mb-3 mt-1">{{music[0].title}}</h2>
            <nuxt-content :document="music[0]" />
          </div>
        </transition>
        <div class="rounded border-purple padding lg:hidden max-w-prose mx-auto -mt-16">
          <h2 class="mb-3 mt-1">{{music[0].title}}</h2>
          <nuxt-content :document="music[0]" />
        </div>
      </nuxt-link>
    </div>

    <div id="editorial" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'editorial'" @mouseleave="hovering = null">
      <nuxt-link  to="/category/editorial">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/editorial.png" alt="Editorial" />
        <transition name="pop-down">
          <div id="editorial-info" class="relative gut-info rounded border-purple padding" v-show="hovering == 'editorial'">
            <h2 class="mb-3 mt-1">{{editorial[0].title}}</h2>
            <nuxt-content :document="editorial[0]" />
          </div>
        </transition>
        <div class="rounded border-purple padding lg:hidden max-w-prose mx-auto -mt-16">
          <h2 class="mb-3 mt-1">{{editorial[0].title}}</h2>
          <nuxt-content :document="editorial[0]" />
        </div>
      </nuxt-link>
    </div>

    <div id="budget" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'budget'" @mouseleave="hovering = null">
      <nuxt-link  to="/category/budget">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/budget.png" alt="Budget" />
        <transition name="pop-down">
          <div id="budget-info" class="relative gut-info rounded border-purple padding" v-show="hovering == 'budget'">
            <h2 class="mb-3 mt-1">{{budget[0].title}}</h2>
            <nuxt-content :document="budget[0]" />
          </div>
        </transition>
        <div class="rounded border-purple padding lg:hidden max-w-prose mx-auto -mt-16">
          <h2 class="mb-3 mt-1">{{budget[0].title}}</h2>
          <nuxt-content :document="budget[0]" />
        </div>
        </nuxt-link>
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

.gut-image {
  max-width: 150px;
  max-height: 150px;
}

/* 'lg': '1024px', */
@media (min-width: 1024px) {

  .gut-image {
    max-width: unset;
    max-height: unset;
  }

  .gut-element {
    min-width: 150px;
    min-height: 150px;
    width: 10vw;
    height: 10vw;
  }

  .gut-info {
    margin-top: -25%;
    right: -25%;
    max-width: 400px;
    width: 200%;
    z-index: 40;
  }

  #editorial-info {
    margin-top: 0%;
    left: -70%;
    top: -300%;
  }

  #venue-info {
    top: -230%;
    right: -50%;
  }

  #budget-info {
    left: -150%;
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
