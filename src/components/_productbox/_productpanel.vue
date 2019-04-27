<template>
  <div class="">
    <div class="productpanel__wrapper" :class="productpanel_wrapper_cls">
      {{showExtendedView}}
      <br>
      more
      <br>
      <productalternates v-if="productdata.alternates"
                          :alternates="productdata.alternates"
                          ></productalternates>

      
    </div>
    <div v-if="productdata.price && productdata.price.sale"
         :class="sale_badge_cls"
         class="sale__badge">- {{compute_sale_percentage}}%</div>
  </div>
</template>

<script>
import productalternates from './_productalternates.vue';
export default {
  name: 'productpanel',
  props: ['productdata', 'showExtendedView'],
  components: {
    productalternates
  },
  computed: {
    productpanel_wrapper_cls() {
      return {
        'extended--simple' : this.showExtendedView && !this.productdata.alternates,
        'extended--alternates' : this.showExtendedView && this.productdata.alternates
      }
    },
    compute_sale_percentage() {
      return Math.round(this.productdata.price.sale.gross / this.productdata.price.gross * 100)
    },
    sale_badge_cls() {
      return {
        'up--simple' : this.showExtendedView && !this.productdata.alternates,
        'up--extended' : this.showExtendedView && this.productdata.alternates
      }
    }
  },
  methods: {
  }
}
</script>

<style lang="sass">
  .productpanel__wrapper
    background-color: red
    position: absolute
    left: 15px
    right: 15px
    bottom: 0
    z-index: 2
    transform: translateY(30px)
    min-height: 30px
    max-height: 30px
    transition: all .25s ease
    background-color: white
    padding: 3px
    z-index: 50
    overflow: hidden
    &.extended--simple,
    &.extended-alternates
      max-height: none
    &.extended--simple
      min-height: 80px
    &.extended--alternates
      min-height: 150px
      


  .sale
    &__badge
      position: absolute
      bottom: 40px
      color: red
      padding: 5px
      z-index: 3
      background-color: white
      font-weight: bold
      font-size: 12px
      transition: all .25s ease
      &.up--simple
        bottom: 90px
      &.up--extended
        bottom: 130px
</style>
