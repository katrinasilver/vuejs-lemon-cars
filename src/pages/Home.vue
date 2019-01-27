<template>
  <div class="home">
    <div class="row p-0 m-0">

      <div class="filters col-md-12 col-lg-3 p-3">
        <form >
          <input id="findCar" v-model="search" class="form-control mr-sm-2" type="search" placeholder="Find the car of your fever dreams...">
        </form>
      </div>

      <div class="shadow-lg cars col-md-12 col-lg-9 row p-0 m-0">
        <ProductGrid v-for="car in findCar" :key="car.id"
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
import ProductGrid from '@/components/ProductGrid'
// import Search from '@/components/Search'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    ProductGrid
    // Search
  },

  data() {
    return {
      search: '',
      cars: []
    }
  },

  created() {
    this.fetchCars()
  },

  computed: {
    findLength() {
      return this.findCar.length
    },

    findCar() {
      return this.cars.filter(car =>
        Object.values(car).reduce((i, c) => i || (typeof c === 'string' && c.toLowerCase()
          .includes(this.search.toLowerCase())), false)
      )
    }
  },

  methods: {
    async fetchCars() {
      try {
        let response = await axios.get(`http://localhost:3000/cars`)
        this.cars = response.data
      } catch(err) {
        console.log(err)
      }
    }
  }
}
</script>
