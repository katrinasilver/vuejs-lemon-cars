<template>
  <div class="mt-4" v-cloak>
    <h4>Vehicle Specs</h4>
    <table class="table">
      <tbody>
        <tr>
          <th scope="row">Transmission:</th>
          <td>{{ transmission }} Transmission</td>
        </tr>
        <tr>
          <th scope="row">Type:</th>
          <td>{{ doors }}, {{ type }}, {{ tag_line }}</td>
        </tr>
        <tr>
          <th scope="row">Mileage:</th>
          <td>{{ mileage.toLocaleString('en-IN', { maximumSignificantDigits : 5}) }} mi.</td>
        </tr>
        <tr>
          <th scope="row">Financing:</th>
          <td>{{ getFinancing ? `Available @ ${getDownpayment}% downpayment**` : 'Cash Only' }}</td>
        </tr>
      </tbody>
    </table>
    <p class="small content">{{ description }}</p>
    <small v-show="getFinancing" class="text-white-50">**Based on original price and excludes taxes &amp; fees.</small>

  </div>
</template>

<script>
export default {
  props: ['description', 'tag_line', 'transmission', 'downpayment', 'doors', 'type', 'discount', 'price', 'mileage', 'financing'],
  name: 'Specs',
  computed: {
    getDownpayment() {
      return (this.downpayment*100).toFixed(2)
    },

    getFinancing() {
      return this.financing && this.price > 8000
    }
  }
}
</script>
