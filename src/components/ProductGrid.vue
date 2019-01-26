<template>
  <div class="card border-0 p-0 m-0 col-lg-4 col-md-6 col-sm-12">
    <img :src="main_img" class="card-img-top" :alt="product_name">
    <div class="bg-success card-footer text-center shadow-sm">
      <h4 class="text-white mb-0">{{ product_name }}</h4>
    </div>
    <div class="card-body p-4 border-left">
      <p class="card-title text-success lead">{{ financing ? 'Financing Available!' : `${(discount*100).toFixed(0)}% Off Sticker Price` }}</p>
      <div :style="{ 'text-decoration': 'line-through' }" class="card-text text-muted">${{ price }}</div>
      <h4 class="card-text text-danger">${{ (price - (price * discount)).toFixed(2) }}</h4>
      <div class="mb-3 d-flex justify-content-between align-items-center">
        <div class="small">
          VIN: {{ vin }}
        </div>
        <div class="badge badge-info">
          {{ mileage }} mi.
        </div>
      </div>
      <router-link class="btn btn-outline-success" :to="`/cars/${ id }/${ vin }`">See Details</router-link>
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
    discount: Number,
    mileage: Number
  }
}
</script>

<style lang="scss" scoped>
  .card {
  border-radius: 0;

  .card-img-top {
    border-radius: 0;
  }
}
</style>
