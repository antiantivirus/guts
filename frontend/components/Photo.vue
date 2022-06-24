<template>
  <img :src="optimSrc" :alt="image.alt"/>
</template>

<script>
  export default {
    props: {
      image: Object,
    },
    computed: {
      srcCloudinary() {
        if (this.image.src) {
          return this.image.src.replace("https://res.cloudinary.com/dgen7ni45/image/upload/", "");
        } else {
          return null
        }
      },
      optimSrc(){
        if (this.srcCloudinary) {
          return 'https://res.cloudinary.com/dgen7ni45/image/upload/' + 'q_auto,w_2500,h_2500,c_limit/' + this.srcCloudinary
        } else {
          return null
        }
      }
    }
  }
</script>