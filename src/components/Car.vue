<template>
  <div :class="[vin]" >
    <div class="jumbotron text-white m-0 p-0">
      <img class="car-image" :src="showImage" :alt="product_name">
      <div class="meta p-4 mb-0">
        <h2 class="display-5 text-warning">{{ product_name }}</h2>
        <h3><small class="text-white-50">Sale Price:</small>
          {{ discountedPrice.toLocaleString('en-IN', {style: 'currency', currency: 'USD'}) }}</h3>

        <p class="small">VIN: {{ vin }}</p>
        <div class="interior-img mb-4">
          <picture>
            <img @click="getDisplayImage()" :src="main_img" :alt="product_name" class="img-fluid img-thumbnail mr-2 mb-2" >
            <img @click="getDisplayImage(index)" v-for="(img, index) in product_imgs" :key="index"
            class="img-fluid img-thumbnail mr-2 mb-2"
            :src="product_imgs[index]" :alt="product_name + index">
          </picture>
        </div>

        <button @click="toggleContent" class="btn btn-lg mr-2 mb-2" :class="[ toggle ? 'btn-warning' : 'btn-success' ]">
          {{ toggle ? 'See Vehicle Specs' : 'Schedule a Test Drive' }}
        </button>

        <router-link class="btn btn-lg btn-success mb-2" to="/">Back to Main Page</router-link>

        <transition name="slideRight">
          <Form v-if="toggle" :vin="vin" :product_name="product_name"/>
          <Specs v-else
            :transmission="transmission"
            :downpayment="downpayment"
            :tag_line="tag_line"
            :description="description"
            :doors="doors"
            :type="type"
            :mileage="mileage"
            :financing="financing"
            :discount="discount"
            :price="price"/>
        </transition>
      </div>

    </div>
  </div>
</template>

<script>
import Form from './Form'
import Specs from './Specs'
import axios from 'axios'

export default {
  name: 'Car',
  components: {
    Form,
    Specs
  },
  data() {
    return {
      id: '',
      product_name: '',
      price: '',
      main_img: '',
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
      showImage: ''
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

    getDisplayImage(index) {
      return index !== undefined ? this.showImage = this.product_imgs[index] : this.showImage = this.main_img
    },

    async fetchOneCar() {
      let car = this
      try {
        const customHeader = await axios.create({
          baseURL: `http://localhost:3000/cars`,
          timeout: 1000
        })
        const res = await customHeader(`/${(this.$route.params.id)}`)

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
        car.showImage = res.data.main_img

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
    position: relative;

    .car-image {
      width: fill-available;

      @media only screen and (max-width: 992px) {
        width: 100%;
      }
    }

    .img-thumbnail {
      cursor: pointer;
      height: 100%;
      max-width: 100px;
      width: 100%;
    }

    .meta {
      background: #252525;

      @media only screen and (min-width: 1200px) {
        background: transparentize(#252525, .3);
        top: 3rem;
        right: 3rem;
        position: absolute;
        display: block;
        width: 30%;
      }
    }

    .btn-warning:focus,
    .btn-success:focus {
      box-shadow: none;
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
