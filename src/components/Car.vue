<template>
  <div :class="[vin]">
    <div class="jumbotron text-white mb-0" :style="{'background-image': `url('${main_img}')`}">
      <div class="meta float-right rounded p-4 mb-3 mt-5">
        <h2 class="display-5 text-warning">{{ product_name }}</h2>
        <h3><small class="text-white-50">Sale Price:</small>
          {{ discountedPrice.toLocaleString('en-IN', {style: 'currency', currency: 'USD'}) }}</h3>

        <p class="small">VIN: {{ vin }}</p>
        <div class="interior-img">
          <Picture class="d-flex justify-content-left mb-4"
            :main_img="main_img"
            :product_name="product_name"
            :product_imgs="product_imgs"/>
        </div>

        <button @click="toggleContent" class="btn btn-lg" :class="[ !toggle ? 'btn-warning' : 'btn-success' ]">
          {{ toggle ? 'Back to Vehicle Specs' : 'Schedule a Test Drive'}}
        </button>

        <transition name="slideRight">
          <Form v-if="toggle" v-cloak :vin="vin" :product_name="product_name"/>
          <Specs v-else
            :transmission="transmission"
            :downpayment="downpayment"
            :doors="doors"
            :type="type"
            :mileage="mileage"
            :financing="financing"
            :discount="discount"
            :price="price"/>
        </transition>
      </div>
    </div>
    <div class="box p-3">
      <h4>{{ tag_line }}</h4>
      <p class="content mt-2 hide-md">{{ description }}</p>
    </div>
  </div>

</template>

<script>
import Picture from './Picture'
import Form from './Form'
import Specs from './Specs'
import axios from 'axios'

export default {
  name: 'Car',
  components: {
    Picture,
    Form,
    Specs
  },
  data() {
    return {
      id: '',
      product_name: '',
      main_img: '',
      price: '',
      mileage: '',
      description: '',
      financing: '',
      discount: '',
      tag_line: '',
      transmission: '',
      downpayment: '',
      vin: '',
      doors: '',
      type: '',
      product_imgs: [],
      toggle: false,
    }
  },

  created() {
    this.fetchOneCar()
  },

  computed: {
    discountedPrice() {
      return +(this.price - (this.price * this.discount))
    }
  },

  methods: {
    toggleContent() {
      this.toggle = !this.toggle
    },

    async fetchOneCar() {
      let car = this
      try {
        const res = await axios.get(`http://localhost:3000/cars/${this.$route.params.id}`)

        car.id = res.data.id
        car.product_name = res.data.product_name
        car.main_img = res.data.main_img
        car.price = res.data.price
        car.mileage = res.data.mileage
        car.description = res.data.description
        car.financing = res.data.financing
        car.discount = res.data.discount
        car.tag_line = res.data.tag_line
        car.type = res.data.type
        car.doors = res.data.doors
        car.vin = res.data.vin
        car.downpayment = res.data.downpayment
        car.transmission = res.data.transmission
        car.product_imgs = res.data.product_imgs

      } catch(err) {
        console.log(err)
      }
    }
  }
}
</script>

<style lang="scss" scoped>

  .jumbotron {
    background-size: cover;
    background-position: center;
    border-radius: 0;
    height: fill-available;

    @media only screen and (min-width: 575px) {
      margin-top: -4rem;
    }

    .meta {
      background: transparentize(#252525, .3);

      @media only screen and (min-width: 960px) {
        display: inline-block;
        max-width: 30%;
      }
    }

    hr {
      background: #e6e6e6;
    }

    h2 {
      font-style: italic;
      text-transform: capitalize;
    }
  }

</style>
