<template>
  <div class="container">
    <div id="home-grid" class="grid lg:grid-cols-2 lg:content-center">
      <img class="drop-shadow-png lg:row-span-2 floating" src="~assets/img/guts.png" />
      <div class="lg:order-last order-first">
        <h1 class="title order-first lg:order-2">
          <img class="drop-shadow-png" alt="guts" src="~assets/img/guts-logo-2.png"/>
        </h1>
        <h2 class="lg:px-8 text-center mx-auto hidden lg:block">A club night with a difference. GUTS lets you prod and poke the internals to see how it works - from budgets, emails and assets to interviews with others working in electronic music.
        <br/>
        Gut exploration and club night coming very soon… 
        </h2>
        <a class="mx-2 lg:mx-auto text-center block PicNic text-3xl lg:text-5xl mt-6 lg:mt-12" href="" target="_blank">Book your tickets</a>
      </div>
    </div>
    <h2 class="max-w-sm text-center mx-auto lg:hidden">GUTS is a transparent club night inviting you into the process blah blah blah blah blah blah blah blah blah blah blah blah</h2>
  </div>
</template>

<script>
export default {
  head() {
  },
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

