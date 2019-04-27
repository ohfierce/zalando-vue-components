<template>
  <div class="index">

    <div class="container">
      <div class="row">
        <div class="col-md-2">
          // sidebar placeholder
        </div>
        <div class="col-md-12">
          <div class="row">
            <productbox v-for="(product,key) in products" 
                        :key=key
                        :productdata=product
                        class="col-md-4"/>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import productbox from '../components/_productbox';
export default {
  name: 'index',
  components: {
    productbox
  },
  data() {
    return {
      products: [
        {
          id: 1,
          articlename: 'Actually Backpack',
          manufacturer: 'Helly Hansen',
          price: {
            net: 100,
            gross: 119,
            sale: false
          },
          images: ['https://mosaic03.ztat.net/vgs/media/pdp-zoom/HE/65/4O/00/2Q/11/HE654O002-Q11@14.jpg', 'https://mosaic04.ztat.net/vgs/media/pdp-zoom/HE/65/4O/00/2Q/11/HE654O002-Q11@16.jpg']
        },
        {
          id: 2,
          articlename: 'This is some jeans',
          manufacturer: 'Levis',
          price: {
            net: 200,
            gross: 239,
            sale: {
              net: 100,
              gross: 119
            }
          },
          images: ['https://mosaic03.ztat.net/vgs/media/pdp-zoom/WR/12/2G/03/IK/17/WR122G03I-K17@10.jpg', 'https://mosaic04.ztat.net/vgs/media/pdp-zoom/WR/12/2G/03/IK/17/WR122G03I-K17@11.jpg'],
        },
        {
          id: 3,
          articlename: 'Generic Product Name',
          manufacturer: 'SomeOther Brand',
          images: ['https://mosaic04.ztat.net/vgs/media/catalog-lg/TO/72/2O/0J/RQ/11/TO722O0JR-Q11@8.jpg', 'https://mosaic04.ztat.net/vgs/media/catalog-sm/TO/72/2O/0J/RQ/11/TO722O0JR-Q11@9.jpg'],
          alternates: [
            {
              
              image: 'https://mosaic03.ztat.net/vgs/media/pdp-zoom/TO/72/2O/0J/RA/11/TO722O0JR-A11@10.jpg',
            },
            {
              image: 'https://mosaic03.ztat.net/vgs/media/pdp-zoom/TO/72/2O/0J/RK/11/TO722O0JR-K11@8.jpg',
            }, 
            {
              image: 'https://mosaic03.ztat.net/vgs/media/pdp-zoom/TO/72/2O/0J/RM/11/TO722O0JR-M11@8.jpg'
            }
          ],
          price: {
            net: 200,
            gross: 239,
            sale: {
              net: 100,
              gross: 119
            }
          },
        },
        {
          id: 4,
          articlename: 'This is some jeans',
          manufacturer: 'Levis',
          price: {
            net: 200,
            gross: 239,
            sale: {
              net: 100,
              gross: 119
            }
          },
          images: ['https://mosaic03.ztat.net/vgs/media/pdp-zoom/WR/12/2G/03/IK/17/WR122G03I-K17@10.jpg', 'https://mosaic04.ztat.net/vgs/media/pdp-zoom/WR/12/2G/03/IK/17/WR122G03I-K17@11.jpg'],
        }
      ]
    }
  }
}
</script>

<style lang="sass">
</style>
