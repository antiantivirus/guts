<template>
  <div class="container">
    <div id="home-grid" class="grid xl:grid-cols-2 xl:content-center">
      <img class="drop-shadow-png xl:row-span-2 floating" src="~assets/img/gutsinside.png" />
      <div class="xl:order-last order-first">
        <div class="rounded border-purple padding">
          <!-- <h3 class="xl:px-8 text-center mx-auto">A club night with a difference. GUTS lets you prod and poke the internals to see how it works - from budgets, emails and assets to interviews with others working in electronic music.</h3> -->
          <h2 ref="type"></h2>
        </div>
        <div class="lg:grid lg:grid-cols-2">
        <a class="mx-2 mx-auto text-center block PicNic mt-6 lg:mt-12" href="https://ra.co/events/1546931" target="_blank">Book your tickets</a>
        <nuxt-link class="mx-2 mx-auto text-center block PicNic mt-6 lg:mt-12" to="/category">Poke around</nuxt-link>
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
  components: {
    Typewriter,
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  data: () => ({
    replace: [
      { from: "...", to: "Hello and welcome to guts" },
      { from: "Hello and welcome to guts", to: "It's nice to have you here :)" },
      { from: "It's nice to have you here :)", to: "We are a club night with a difference." },
      { from: "We are a club night with a difference.", to: "Prod and poke our internals to see how we work - from budgets, emails and assets to interviews with others working in electronic music." },
    ],
  }),
  mounted(){
    var type = this.$refs.type;

    var typewriter = new Typewriter(type, {
      loop: true,
      delay: 75,
      cursor: ''
    });

    typewriter
      .pauseFor(1500)
      .typeString('Hello and welcome to guts')
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
      .typeString("0.18g of CO2 was used to load this website...")
      .pauseFor(400)
      .deleteAll(2)
      .typeString("Lots of people have visited this site but you are our fave...")
      .pauseFor(400)
      .deleteAll(3)
      .typeString("Bleep bloop...OOOWWWWWCCCHHH I stubbed my toe!...")
      .pauseFor(400)
      .start();
      }
};
</script>

<style scoped>

/* 'lg': '1024px', */
@media (min-width: 1024px) {
  #home-grid {
    height: calc(100vh - 14rem);
  }
}

.floating {
  animation: float 8s infinite ease-in-out;
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

</style>

