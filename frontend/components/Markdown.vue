<template>
    <vue-markdown>
      <slot></slot>
    </vue-markdown>
</template>


<script>
import VueMarkdown from 'vue-markdown'
export default ({
  name: 'MyComponent',
  components: {
    VueMarkdown
  }
})
</script>