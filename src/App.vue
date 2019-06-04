<template>
  <div id="app">
    <simple-lightbox/>
    <h1>Type img's url to show in lightbox component</h1>
    <input v-model="imgUrl" type="text" size="100"/> <br/>
    <button @click="openLightbox">
      Click me
    </button>
    <simple-lightbox ref="lightbox"/>
  </div>
</template>

<script>
import SimpleLightbox from './SimpleLightbox.vue'

export default {
  name: 'app',
  components: {
    SimpleLightbox
  },
  data () {
    return {
      imgUrl: 'https://images.unsplash.com/photo-1559538619-79636b249e31?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=80'
    }
  },
  methods: {
    openLightbox () {
      this.$refs.lightbox.show(this.imgUrl)
    }
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
