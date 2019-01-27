<template>
  <div class="home">
    <header class="navbar navbar-expand-lg d-flex justify-content-center">
      <router-link class="navbar-brand" to="/"><h2 class="mb-0 text-warning">Lemon Autos</h2></router-link>
      <p class="mb-0 lead border-left border-muted text-white pr-3 pl-3">Selling your Dream Car at a sketchy lot nearby</p>
      <input id="findCar" v-model="search" class="form-control m-sm-3" type="search" placeholder="Find the car of your fever dreams...">
    </header>

    <div class="row p-0 m-0">
      <div class="cars col-sm-12 row p-0 m-0">
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
    <footer class="bg-dark text-muted p-4 text-center">&copy; 2019 Lemon Autos // Our cars are more than just lemons!</footer>
  </div>
</template>

<script>
import ProductGrid from '@/components/ProductGrid'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    ProductGrid
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
