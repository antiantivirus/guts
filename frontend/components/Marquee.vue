<template>
  <div class="wobble">
    <client-only>
      <marquee-text id="marquee" class="pt-6 pb-10 -mt-2" @mouseover="marqueePaused = true" @mouseleave="marqueePaused = false" :repeat="3" :duration="35" :paused="marqueePaused">
        <span class="text-5xl marquee-text PicNic">The gut goes all the way from your mouth to your bottom ... 0.18g of CO2 was used to load this website ...&nbsp;</span>
      </marquee-text>
    </client-only>
  </div>
</template>

<script>
export default {
  data() {
    return {
      marqueePaused: false,
    }
  },
}
</script>

<style scoped>
  .wobble {
    background-image: url('~assets/img/wobble.svg');
    background-repeat: no-repeat;
    background-position: bottom;
    background-size: cover;
  }
</style>