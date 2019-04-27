<template>
  <div class="productpanel__alternates">
    <productalternate v-for="(alternate, key) in alternates"
                      :alternate="alternate"
                      :key="key"
                      :index="key"
                      ></productalternate>
    
  </div>
</template>

<script>
import productalternate from './_productalternate.vue';
export default {
  name: 'productalternates',
  props: ['alternates'],
  components: {
    productalternate
  }
}
</script>

<style lang="sass">
  .productpanel__alternates
    text-align: left
    pointer-events: auto
</style>
