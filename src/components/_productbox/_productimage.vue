<template>
  <div class="productbox__imagewrapper">
    
    <div class="productbox__image" 
           :style="productbox_image_style" 
           v-if="images"></div>

    <div class="productbox__hoverimage" 
         :style="productbox_hoverimage_style"
         :class="productbox_hoverimage_cls"
         v-if="images[1]"></div>

  </div>
</template>

<script>
export default {
  name: 'productbox',
  props: ['images', 'showHoverImage', 'showAlternateImage'],
  computed: {
    productbox_image_style: function () {
      return {
        backgroundImage: 'url('+this.images[0]+')'
      }
    },
    productbox_hoverimage_style: function() {
      if(this.showAlternateImage) {
        return {
          backgroundImage: 'url('+this.showAlternateImage+')'
        }
      } else {
        return {
          backgroundImage: 'url('+this.images[1]+')'
        }
      }
      
    },
    productbox_hoverimage_cls: function() {
      return {
        'visible':  this.showHoverImage == true
      }
    }
  },
}
</script>

<style lang="sass">
  .productbox
    &__imagewrapper
      width: 100%
      position: relative
      &:after 
        display: block
        content: ''
        padding-bottom: 145%
    &__image,
    &__hoverimage
      position: absolute
      left: 0
      right: 0
      top: 0
      bottom: 0
      background-size: cover
      background-repeat: no-repeat
      background-position: center center

    &__image
      z-index: 1
    
    &__hoverimage
      z-index: 2
      opacity: 0
      
      transition: opacity 0s ease
      
      &.visible
        opacity: 1
        transition: opacity .25s ease
        transition-delay: .25s ease
</style>
