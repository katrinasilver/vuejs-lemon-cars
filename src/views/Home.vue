<template>
  <div class="home">
    <Jumbotron class="mb-0" v-for="car in cars.slice(0, 1)" :key="car.id"
      :main_img="car.main_img"
      :product_name="car.product_name"
      :tag_line="car.tag_line"
      :description="car.description"
    />
    <div class="products row">
      <ProductGrid v-for="car in cars.slice(1, 16)" :key="car.id"
        :main_img="car.main_img"
        :product_name="car.product_name"
        :price="car.price"
        :tag_line="car.tag_line"
        :financing="car.financing"
        :vin="car.vin"
        :discount="car.discount"
      />
    </div>
  </div>
</template>

<script>
import ProductGrid from '@/components/ProductGrid.vue'
import Jumbotron from '@/components/Jumbotron.vue'

export default {
  props: ['cars'],
  name: 'home',
  components: {
    ProductGrid,
    Jumbotron
  }
}
</script>

<style lang="scss">
  .card {
    border-radius: 0;

    .card-img-top {
      border-radius: 0;
    }
  }
</style>
