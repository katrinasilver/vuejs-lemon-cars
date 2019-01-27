<template>
  <transition name="slideUp">
    <div v-cloak class="card border-white p-0 m-0 col-lg-4 col-md-6 col-sm-12">
      <img :src="main_img" class="card-img-top" :alt="product_name">
      <div class="bg-secondary card-footer text-center shadow-sm">
        <h4 class="text-white mb-0">{{ product_name }}</h4>
        <div class="small text-white-50">
          VIN: {{ vin }}
        </div>
      </div>
      <div class="card-body p-4">
        <p class="card-title text-success lead">{{ `${getDiscount}% Off Sticker Price` }}</p>
        <div :style="{ 'text-decoration': 'line-through' }" class="card-text text-muted">
          {{ price.toLocaleString('en-IN', { style: 'currency', currency: 'USD'}) }}</div>

        <h4 class="card-text text-danger">{{ discountedPrice.toLocaleString('en-IN', {style: 'currency', currency: 'USD'}) }}</h4>

        <div class="mb-3 d-flex justify-content-left align-items-center">
          <span v-if="discountedPrice < 2500" class="badge badge-danger mr-1">
            Clearance!
          </span>
          <span v-if="mileage < 40000" class="badge badge-primary mr-1">
            Low Miles!
          </span>
          <span v-if="discount >= .25" class="badge badge-warning mr-1">
            Huge Price Drop!
          </span>
          <span v-if="financing && price > 8000" class="badge badge-success mr-1">
            Financing OK
          </span>
        </div>
        <router-link class="btn btn-outline-success" :to="{ name: 'cars', params: { id, vin } }">See Details</router-link>
      </div>
    </div>
  </transition>
</template>

<script>

export default {
  props:['search'],
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
  },

  computed: {
    getDiscount() {
      return (this.discount*100).toFixed(0)
    },

    discountedPrice() {
      return +(this.price - (this.price * this.discount))
    }
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
