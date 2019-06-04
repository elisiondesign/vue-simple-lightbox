# vue-sole-lightbox
This a simple and minimalistic zero-dependency Vue.js lightbox. The only aim is to fill the screen with a single image while dimming the surroundings. That's it.

If you seek a lightbox component with navigation and customizable controls, this component is not a good choice.
On the other hand, if you only need to highlight a single image at any given time (after a click event for example), than this might be the way to go.

You can find a demo on [codepen](https://codepen.io/sindael/pen/Ybgvre).

## Getting started
```
npm i @elisiondesign/vue-sole-lightbox
```

## Usage
You can include the component anywhere within the template. Just make sure that the `ref` attribute is present.

```vue
<template>
    <div>
    // Some code

    <sole-lightbox ref="lightbox"/>
    </div>
</template>

<script>
import SoleLightbox from 'vue-sole-lightbox'

export default {
  components: {
    // ...
    SoleLightbox,
  },

  // ...
}
</script>
```

## Example
```vue
<template>
  <div id="app">
    <h1>Type img's url to show in lightbox component</h1>
    <input v-model="imgUrl" type="text" size="100"/> <br/>
    <button @click="openLightbox">
      Click me
    </button>
    <sole-lightbox ref="lightbox"/>
  </div>
</template>

<script>
import SoleLightbox from './SoleLightbox.vue'

export default {
  name: 'app',
  components: {
    SoleLightbox
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
```

## Available props:

| Prop           | Type              | Value                                                           |
| -------------- | ----------------- | --------------------------------------------------------------- |
| prefix         | string            | **(Optional)** prefix image path (e.g. '/images/')              |

## Available methods through $refs:
| Method        | Arguments                                  | Description                                   |
| ------------- | ---------------------------------------------- | ----------------------------------------- |
| show          | img - path to image<br>altText - image caption | Displays Lightbox with given image        |
| hide          | _none_                                         | Hides Lightbox                            |