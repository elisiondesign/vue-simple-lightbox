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

You should also include the `css` file. 

```
@import "node_modules/@elisiondesign/vue-sole-lightbox/dist/SoleLightbox";
```

However, if you wish you can style the component by yourself.
See [styles](#styles) to explore the default styling.

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

<style>
  @import "node_modules/@elisiondesign/vue-sole-lightbox/dist/SoleLightbox";
</style>
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

## Styles
Default styles.
```css
.lightbox {
    position: fixed;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, .9);
    width: 100%;
    height: 100%;
    display: -webkit-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 200;
    color: rgba(255,255,255,0.8);
}
.lightbox-close {
    position: fixed;
    z-index: 210;
    right: 0;
    top: 0;
    padding: 1rem;
    font-size: 1.7rem;
    cursor: pointer;
    width: 4rem;
    height: 4rem;
    color: white;
}
.lightbox-main {
    display: -webkit-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
    width: 100%;
    height: 100%;
}

.lightbox-image-container {
    -webkit-box-flex: 1;
    width: 20%;
    -webkit-flex: 1;
    -ms-flex: 1;
    flex: 1;
}
.lightbox-image {
    width: 100%;
    height: 100%;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: 50% 50%;
}
.lightbox-caption {
    position: absolute;
    bottom: 15px;
    width: 100%;
    z-index: 100;
    text-align: center;
    text-shadow: 1px 1px 3px rgb(26, 26, 26);
}
.lightbox-caption span {
    border-radius: 12px;
    background-color: rgba(0, 0, 0, .6);
    padding: 2px 10px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

.lightbox-fade-enter-active,
.lightbox-fade-leave-active {
    transition: all 0.4s ease;
}
.lightbox-fade-enter,
.lightbox-fade-leave-to {
    opacity: 0;
}
```
