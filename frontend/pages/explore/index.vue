<template>
  <div id="the-gut" class="container relative">
    <div id="promo" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'promo'" @mouseleave="hovering = null">
      <div class="relative">
      <nuxt-link to="/explore/promo">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/promo.png" alt="Promo" />
        <transition name="pop-down">
          <div class="absolute gut-info rounded border-purple padding" v-show="hovering == 'promo'">
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
    </div>

    <div id="venue" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'venue'" @mouseleave="hovering = null">
      <div class="relative">
      <nuxt-link to="/explore/venue">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/venue.png" alt="Venue" />
        <transition name="pop-down">
          <div id="venue-info" class="gut-info rounded border-purple padding" v-show="hovering == 'venue'">
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
    </div>

    <div id="music" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'music'" @mouseleave="hovering = null">
      <div class="relative">
      <nuxt-link  to="/explore/music">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/music.png" alt="Music" />
        <transition name="pop-down">
          <div class="gut-info rounded border-purple padding" v-show="hovering == 'music'">
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
    </div>

    <div id="editorial" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'editorial'" @mouseleave="hovering = null">
      <div class="relative">
        <nuxt-link  to="/explore/editorial">
          <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/editorial.png" alt="Editorial" />
          <transition name="pop-down">
            <div id="editorial-info" class="gut-info rounded border-purple padding" v-show="hovering == 'editorial'">
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
    </div>

    <div id="budget" class="gut-element lg:absolute mb-6 lg:mb-0" @mouseenter="hovering = 'budget'" @mouseleave="hovering = null">
      <div class="relative">
      <nuxt-link  to="/explore/budget">
        <img class="drop-shadow-png gut-image ml-auto mr-0" src="/guts/budget.png" alt="Budget" />
        <transition name="pop-down">
          <div id="budget-info" class="gut-info rounded border-purple padding" v-show="hovering == 'budget'">
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
  </div>
</template>


<script>

export default ({
  head() {
    return {
      title: 'INSIDE THE GUTS',
    }
  },
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
  mounted(){
    const gutsAppear = this.$gsap.timeline()
    gutsAppear.to('.gut-element', {
      scale: 1,
      ease: 'Back.easeOut',
      delay: 0.5,
      stagger: {
        each: 0.2,
      }
    })
  }
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

  .gut-element {
    transform: scale(0);
    z-index: 0;
  }

  .gut-element:hover {
    z-index: 20;
  }

  #the-gut {
    height: calc(100vh - 200px);
    max-height: 1200px;
  }

  .gut-image {
    max-width: 100%;
    max-height: 100%;
  }

  .gut-element {
    /* min-width: 150px; */
    /* min-height: 150px; */
    width: 12vw;
    height: 12vw;
  }

  .gut-info {
    margin-top: -25%;
    /* right: -25%; */
    max-width: 400px;
    width: 200%;
    z-index: 40;
    position: absolute;
  }

  #editorial-info {
    /* top: 0px;
    left: 0px;
    transform: translate(-50%, -135%); */
    /* bottom: 100%;
    right: 100%; */
    bottom: 58%;
    right: 38%;
  }

  #venue-info {
    bottom: 50%;
    left: 67%;
  }

  #budget-info {
    right: 50%;
  }

  #promo {
    top: 2%;
    left: 4%
  }

  #venue {
    bottom: 10%;
    left: 25%;
  }

  #music {
    top: 15%;
    left: 38%
  }

  #editorial {
    bottom: 12%;
    right: 20%;
    width: 16vw;
    height: 16vw;
  }

  #budget {
    top: 10%;
    right: 10%;
  }
}
</style>
