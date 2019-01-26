<template>
  <div class="car">
    <Car v-for="car in cars.filter(car => car.id === $route.params.id)"
      :key="car.id"
      :id="car.id"
      :main_img="car.main_img"
      :product_name="car.product_name"
      :price="car.price"
      :tag_line="car.tag_line"
      :financing="car.financing"
      :vin="car.vin"
      :discount="car.discount"
      :mileage="car.mileage"
      :description="car.description"
    />
  </div>
</template>

<script>
import Car from '@/components/Car'
export default {
  props: ['cars'],
  name: 'cars',
  components: {
    Car
  }
}
</script>
