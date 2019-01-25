<template>
  <div id="app">
    <Header />
    <router-view :cars="cars"/>
    <footer class="bg-dark text-muted p-5 text-center">&copy; 2019 Cheap Cars</footer>
  </div>
</template>

<script>
  import Header from '@/components/Header.vue'
  import axios from 'axios'

  export default {
    name: 'cheap-cars',

    components: {
      Header
    },

    data() {
      return {
        cars: [],
        showError: false
      }
    },

    created() {
      this.fetchCars()
    },

    methods: {
      async fetchCars() {
        const url = `https://my.api.mockaroo.com/cars.json?key=5833a0e0`
        try {
          let response = await axios.get(url)
          this.cars = response.data
        } catch(err) {
          console.log(err)
          showError: true
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
