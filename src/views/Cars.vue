<template>
  <div class="cars container">
    <h1>This is the all cars page</h1>
    <Car />
  </div>
</template>

<script>
import Car from '@/components/Car.vue'

export default {
  name: 'cars',
  components: {
    Car
  }
}
</script>
