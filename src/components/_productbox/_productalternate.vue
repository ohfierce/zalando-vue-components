<template>
  <div class="productpanel_alternate" 
       @mouseenter="fadeInAlternate()"
       @mouseleave="fadeOutAlternate()"
       :class="alternate_hover_cls">
    <img :src="alternate.image" alt="">
  </div>
</template>

<script>
export default {
  name: 'productalternate',
  props: ['alternate', 'index'],
  data() {
    return {
      alternateHovered: false
    }
  },
  computed: {
    alternate_hover_cls: function() {
      return {
        'hovered' : this.alternateHovered
      }
    }
  },
  methods: {
    fadeInAlternate() {
      this.alternateHovered = true
      this.$parent.$parent.$emit('switchPreviewToAlternate', this.index)
    },
    fadeOutAlternate() {
      this.alternateHovered = false
      this.$parent.$parent.$emit('removeAlternatePreview')
    }
    
  }
}
</script>

<style lang="sass">
  .productpanel_alternate 
    background-color: white
    display: inline-block
    padding-right: 5px
    opacity: .2
    transition: opacity .25s ease
    &.hovered
      opacity: 1
    img
      width: 40px
      height: auto
</style>
