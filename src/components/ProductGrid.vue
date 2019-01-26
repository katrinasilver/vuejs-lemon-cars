<template>
  <div class="card border-0 p-0 m-0 col-lg-4 col-md-6 col-sm-12">
    <img :src="main_img" class="card-img-top" :alt="product_name">
    <div class="bg-secondary card-footer text-center shadow-sm">
      <h4 class="text-white mb-0">{{ product_name }}</h4>
    </div>
    <div class="card-body p-4 border-left">
      <p class="card-title text-success lead">{{ `${(discount*100).toFixed(0)}% Off Sticker Price` }}</p>
      <div :style="{ 'text-decoration': 'line-through' }" class="card-text text-muted">${{ price }}</div>
      <h4 class="card-text text-danger">${{ (price - (price * discount)).toFixed(2) }}</h4>
      <div class="mb-3 d-flex justify-content-between align-items-center">
        <div class="small">
          VIN: {{ vin }}
        </div>
        <span v-if="mileage < 50000" class="badge badge-primary">
          Low Miles!
        </span>
        <span v-if="discount >= .30" class="badge badge-danger">
          Clearance Price!
        </span>
        <span v-if="financing && price > 5000" class="badge badge-success">
          Financing Available
        </span>
      </div>
      <router-link class="btn btn-outline-success" :to="{ name: 'cars', params: { id } }">See Details</router-link>
    </div>
  </div>
</template>

<script>

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
