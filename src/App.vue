<template>
  <div id="app">
    <Header />
    <router-view :cars="cars"/>
    <footer class="bg-dark text-muted p-4 text-center">&copy; 2019 Lemon Autos // Our cars are more than just lemons!</footer>
  </div>
</template>

<script>
  import Header from '@/components/Header.vue'
  import axios from 'axios'

  export default {
    name: 'lemon-autos',

    components: {
      Header
    },

    data() {
      return {
        cars: []
      }
    },

    created() {
      this.fetchCars()
    },

    methods: {
      async fetchCars() {
        const url = `http://localhost:3000/cars`
        try {
          let response = await axios.get(url)
          this.cars = response.data
        } catch(err) {
          console.log(err)
        }
      }
    }
  }
</script>

<style lang="scss">
  @import '../node_modules/bootstrap/scss/bootstrap.scss';
  @import '../sass/custom.scss';

  [v-cloak] {
    display: none;
  }

  body {
    text-rendering: optimizeLegibility;
  }
</style>
