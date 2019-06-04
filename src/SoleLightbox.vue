
<template>
  <div>
    <transition name="lightbox-fade">
      <div v-if="visible" class="lightbox" @click="hide">
        <div class="lightbox-close">
          &times;
        </div>
        <transition name="lightbox-fade">
          <div v-show="altText !== ''" class="lightbox-caption">
            <span>{{ altText }}</span>
          </div>
        </transition>
        <div class="lightbox-main">
          <div class="lightbox-image-container">
            <transition mode="out-in">
              <div class="lightbox-image" :style="{ 'backgroundImage':'url(' + path + ')'}" />
            </transition>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    prefix: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      visible: false, // Lightbox not visible by default
      imagePath: '', // Path to image
      altText: '' // Image Caption Text
    }
  },
  computed: {
    path () {
      return `${this.prefix}${this.imagePath}`
    }
  },
  methods: {
    show (imagePath, altText = '') {
      this.visible = true
      this.imagePath = imagePath
      this.altText = altText
    },
    hide () {
      this.visible = false
    }
  }
}
</script>

<style>
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
</style>
