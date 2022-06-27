<template>
  <div>
    <div id="bg"></div>
    <nuxt-link  to="/">
      <img class="mx-auto" id="logo" ref="logo" src="~assets/img/guts-logo.png"/>
    </nuxt-link>
    <!-- <Marquee /> -->
    <div class="mt-8 invisible opacity-0" ref="content">
      <Nuxt />
    </div>
    <footer class="mt-16 mb-16" ref="footer">
      <img id="footer-logo" class="mx-auto footer-logo" src="~assets/img/supported.svg" alt=""/>
    </footer>
  </div>
</template>

<script>
export default ({
  mounted(){
    this.introAnim()
  },
  methods: {
    introAnim(){
      // this.$gsap.to(this.$refs.logo, { duration: 0, scale: 0, delay: 0 })
      // this.$gsap.to(this.$refs.logo, { duration: 0.75, scale: 1, delay: 0 })
      // this.$gsap.to(this.$refs.logo, { duration: 0.5, scale: 2, delay: 0 })
      this.$gsap.to(this.$refs.logo, { duration: 2, y: '-42vh', delay: 1, ease: 'Back.easeOut' })
      // this.$gsap.to(this.$refs.logo, { duration: 1, scale: 1, delay: 0.5 })
      this.$gsap.to(this.$refs.content, { duration: 0.5, visibility:"visible", opacity: 1, delay: 2.5 })
      // this.$gsap.to(this.$refs.footer, { duration: 1, visibility:"visible", opacity: 1, delay: 1.75 })
    }
  }

})
</script>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

#bg {
  background-image: url('~assets/img/background-compressed.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  filter: blur(15px);
  -webkit-filter: blur(15px);
  z-index: -1;
}

#logo {
  max-width: 238px;
}

#footer-logo {
  max-width: 150px;
}

#logo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>
