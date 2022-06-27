<template>
  <div class="xl:container mb-24 md:mb-72 xl:mb-0">
    <div id="home-grid" class="grid xl:grid-cols-2 xl:content-center">
      <img ref="character" id="character" class="drop-shadow-png floating max-w-lg mx-auto w-full" src="~assets/img/gutsinside.png" />
      <div ref="bubble" class="flex justify-center flex-col">
        <div>
          <div id="speech-bubble" class="fixed w-screen bottom-0 xl:static xl:w-full rounded border-purple padding">
            <!-- <h3 class="xl:px-8 text-center mx-auto">A club night with a difference. GUTS lets you prod and poke the internals to see how it works - from budgets, emails and assets to interviews with others working in electronic music.</h3> -->
            <h2 ref="type" class="h2-large"></h2>
          </div>
          <div class="xl:mt-2 max-w-lg mx-auto xl:max-w-none">
          <!-- <a class="mx-2 mx-auto text-center block PicNic mt-6 lg:mt-0 button padding w-full" href="https://ra.co/events/1546931" target="_blank">Book your tickets</a> -->
          <nuxt-link class="mx-2 mx-auto text-center block PicNic mt-6 lg:mt-0 button padding w-full" to="/explore" >Poke around</nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <!-- <h2 class="max-w-sm text-center mx-auto lg:hidden">
      A club night with a difference. GUTS lets you prod and poke the internals to see how it works - from budgets, emails and assets to interviews with others working in electronic music.
        <br/>
      Gut exploration and club night coming very soon… 
    </h2> -->
  </div>
</template>

<script>
import Typewriter from 'typewriter-effect/dist/core';

export default {
  transition: {
    name: 'inside',
  },
  components: {
    Typewriter,
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  methods:{
    enterGuts(){
      this.$gsap.to(this.$refs.bubble, { duration: 1, opacity: 0, ease: 'easeOut' })
      this.$gsap.to(this.$refs.character, { duration: 1, xPercent: 63, delay: 0.75, ease: 'easeOut' })
      this.$gsap.to(this.$refs.character, { duration: 1.5, scale: 20, delay: 1.8, ease: 'easeOut' })
    }
  },
  mounted(){
    var type = this.$refs.type;

    var typewriter = new Typewriter(type, {
      loop: true,
      delay: 75,
      cursor: ''
    });

    typewriter
      .pauseFor(1800)
      .typeString('Hello and welcome to GUTS')
      .pauseFor(400)
      .deleteAll(2)
      .typeString("It's nice to have you here :)")
      .pauseFor(400)
      .deleteAll(4)
      .typeString('We are a club night with a difference.')
      .pauseFor(400)
      .deleteAll(2)
      .typeString("Prod and poke our internals to see how we work - from budgets, emails and assets to interviews with others working in electronic music.")
      .pauseFor(400)
      .deleteAll(3)
      .typeString("0.18g of CO2 was used to load this website.")
      .pauseFor(400)
      .deleteAll(2)
      .typeString("Lots of people have visited this site but you are our fave.")
      .pauseFor(400)
      .deleteAll(3)
      .typeString("Bleep bloop...OOOWWWWWCCCHHH I stubbed my toe!")
      .pauseFor(400)
      .start();
      }
};
</script>

<style scoped>

#speech-bubble {
  min-height: 20vh;
  /* margin-left: -1rem; */
}

.floating {
  animation: float 8s infinite ease-in-out;
}

#character {
  transform-origin: 49% 60%;
}


@keyframes float {
	0% {
		/* box-shadow: 0 5px 15px 0px rgba(0,0,0,0.6); */
		transform: translatey(10px);
	}
	50% {
		/* box-shadow: 0 25px 15px 0px rgba(0,0,0,0.2); */
		transform: translatey(-10px);
	}
	100% {
		/* box-shadow: 0 5px 15px 0px rgba(0,0,0,0.6); */
		transform: translatey(10px);
	}
}

.inside-leave-active {
  transition: opacity 2s ease-in;
}

.inside-enter-active {
  transition: opacity 1s ease-in;
}

.inside-enter, .inside-leave-active {
  opacity: 0; 
}

/* 'lg': '1024px', */
@media (min-width: 1024px) {
  #home-grid {
    height: calc(100vh - 350px);
  }

}

/* 'xl': '1280px', */
@media (min-width: 1280px) {

  #speech-bubble {
    min-height: 200px;
    margin-left: 0rem;
  }
}


</style>

