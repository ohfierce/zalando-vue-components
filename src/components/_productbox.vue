<template>
  <div class="productbox" 
       @mouseenter="onMouseEnter"
       @mouseleave="onMouseLeave">
      
       
    <productimage :images="productdata.images" 
                  :showHoverImage="showHoverImage"
                  :showAlternateImage="showAlternateImage"></productimage>

    
    <productpanel :productdata="productdata"
                  :showExtendedView="showExtendedProductPanel"
                  v-on:switchPreviewToAlternate="switchPreviewToAlternate"
                  v-on:removeAlternatePreview="removeAlternatePreview"></productpanel>
  </div>
</template>

<script>
import productimage from './_productbox/_productimage'
import productpanel from './_productbox/_productpanel'
export default {
  name: 'productbox',
  components: {
    productimage,
    productpanel
  },
  props: ['productdata'],
  data() {
    return {
      isHovered: false,
      showExtendedProductPanel: false,
      showHoverImage: false,
      showAlternateImage: null,
    
    }
  },
  computed: {
    showHoverImage_computed() {
      return this.showHoverImage
      
    }
  },
  methods: {
    switchPreviewToAlternate(index) {
      this.showAlternateImage = this.productdata.alternates[index].image
    },
    removeAlternatePreview() {
      this.showAlternateImage = null
    },
    onMouseEnter() {
      this.isHovered = true
      console.log('entered productbox with id'+this.productdata.id)
      this.showExtendedProductPanel = this.isHovered
      setTimeout(() => {
        
          this.showHoverImage = this.isHovered
        
      }, 300)
    },

    onMouseLeave() {
      this.isHovered = false
      console.log('left productbox with id'+this.productdata.id)
      this.showExtendedProductPanel = this.isHovered

      this.showHoverImage = this.isHovered
      setTimeout(() => {
        this.showHoverImage = this.isHovered
      }, 300)
    }

  }
}
</script>

<style lang="sass">
  .productbox
    margin-bottom: 50px
    position: relative
    &__inner  
      

</style>
