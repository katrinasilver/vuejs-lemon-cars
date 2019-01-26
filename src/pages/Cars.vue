<template>
  <div class="car">
    <Car />
  </div>
</template>

<script>
import Car from '@/components/Car'
export default {
  props: ['cars'],
  name: 'cars',
  components: {
    Car
  },

  // created() {
  //   this.getOneCar()
  // },

  // methods: {
  //   getOneCar() {
  //     return this.cars.filter(car => car.id === this.$route.params.id)
  //   }
  // }
}
</script>
