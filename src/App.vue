<template>
  <div id="app">
    <simple-lightbox/>
  </div>
</template>

<script>
import SimpleLightbox from './SimpleLightbox.vue'

export default {
  name: 'app',
  components: {
    SimpleLightbox
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
