<template>
  <div class="home">
    <transition name="slideRight">
      <Jumbotron class="mb-0" v-cloak v-for="car in cars.slice(0, 1)" :key="car.id"
        :id="car.id"
        :main_img="car.main_img"
        :product_name="car.product_name"
        :tag_line="car.tag_line"
        :description="car.description"
        :vin="car.vin"
      />
    </transition>

    <Search />

    <div class="row p-0 m-0">
      <div class="filters col-md-12 col-lg-3 p-3">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quos distinctio blanditiis quo magni recusandae in minus quae dignissimos,
         temporibus similique et, error commodi sunt! Dicta libero pariatur quis facilis magnam.
      </div>

      <div is="transition-group" name="slideUp" v-cloak class="cars col-md-12 col-lg-9 row p-0 m-0">

        <ProductGrid v-for="car in cars.slice(1, 16)" :key="car.id"
          :id="car.id"
          :main_img="car.main_img"
          :product_name="car.product_name"
          :price="car.price"
          :tag_line="car.tag_line"
          :financing="car.financing"
          :vin="car.vin"
          :discount="car.discount"
          :mileage="car.mileage"
        />

      </div>

    </div>
  </div>
</template>

<script>
import Jumbotron from '@/components/Jumbotron'
import ProductGrid from '@/components/ProductGrid'
import Search from '@/components/Search'

export default {
  props: ['cars'],
  name: 'home',
  components: {
    Jumbotron,
    ProductGrid,
    Search
  }
}
</script>

<style lang="scss">

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
