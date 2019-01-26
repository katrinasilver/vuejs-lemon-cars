<template>
  <div>
    <img :src="main_img" :alt="product_name">
    <p>{{ product_name }}</p>
  </div>
</template>

<script>
export default {
  name: 'Car',
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
