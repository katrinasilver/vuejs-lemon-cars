<template>
  <div>
    <!-- <img :src="main_img" :alt="product_name"> -->
    <p>{{ product_name }}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Car',

  data() {
    return {
      product_name: ''
    }
  },

  created() {
    this.fetchOneCar()
  },

  methods: {
    async fetchOneCar() {
      const url = `http://localhost:3000/cars/${this.$route.params.id}`
      let car = this
      try {
        let response = await axios.get(url)
        car.product_name = response.data.product_name
      } catch(err) {
        console.log(err)
      }
    }
  }
}
</script>
