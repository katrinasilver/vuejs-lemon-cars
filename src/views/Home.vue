<template>
  <div class="home">
    <transition name="slideRight">
      <Jumbotron class="mb-0" v-cloak v-for="car in cars.slice(0, 1)" :key="car.id"
        :main_img="car.main_img"
        :product_name="car.product_name"
        :tag_line="car.tag_line"
        :description="car.description"
      />
    </transition>
    <div is="transition-group" name="slideUp" v-cloak class="products row">
      <ProductGrid v-for="car in cars.slice(1, 16)" :key="car.id"
        :id="car.id"
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

  .slideUp-enter,
  .slideUp-leave-to {
    transform: translateY(150px) rotate(0deg);
    opacity: 0;
  }

  .slideUp-enter-active,
  .slideUp-leave-active {
    transition: all .3s linear;
  }

  .slideRight-leave-to,
  .slideRight-enter {
    transform: translate(150px) rotate(0deg);
    opacity: 0;
  }

  .slideRight-enter-active,
  .slideRight-leave-active {
    transition: all .3s ease;
  }


</style>
