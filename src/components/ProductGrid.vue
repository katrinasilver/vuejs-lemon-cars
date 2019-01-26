<template>
  <div class="card border-white p-0 col-lg-4 col-md-6 col-sm-12" >
    <img :src="main_img" class="card-img-top" :alt="product_name">
    <div class="border card-footer text-center">
      <h5 class="text-muted mb-0">{{ financing ? 'Financing Available!' : `${(discount*100).toFixed(0)}% Off Sticker Price` }}</h5>
    </div>
    <div class="card-body p-4 border border-top-0">
      <p class="card-title lead">{{ product_name }}</p>
      <div :style="{ 'text-decoration': 'line-through' }" class="card-text text-muted">${{ price }}</div>
      <h4 class="card-text text-danger">${{ (price - (price * discount)).toFixed(2) }}</h4>
      <div class="mb-3 small">VIN: {{ vin }}</div>
      <!-- <button class="btn btn-success">See More</button> -->
      <router-link class="btn btn-success" :to="`/cars/${ id }`">See More</router-link>
    </div>
  </div>
</template>

<script>
import Car from './Car'

export default {
  name: 'ProductGrid',
  props: {
    id: Number,
    product_name : String,
    main_img : String,
    tag_line: String,
    vin: String,
    financing : Boolean,
    price : Number,
    discount: Number
  },
}
</script>
