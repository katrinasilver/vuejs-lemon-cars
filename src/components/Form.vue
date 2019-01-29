<template>
  <div class="test-drive">
    <form v-show="!submitted" v-cloak class="test-drive mt-4 was-validated">
      <div class="form-group">
        <label for="name">Your Name</label>
        <input type="text" v-model="name" class="form-control" id="name" placeholder="enter your full name" required autofocus>
      </div>
      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" v-model="email" class="form-control" id="email" placeholder="your@example.com" required>
      </div>
      <div class="form-group">
        <label for="phone">Phone</label>
        <input type="tel" v-model="phone" class="form-control" id="phone" placeholder="123-456-7890" required>
      </div>
      <button type="submit" @click.prevent="process" class="btn btn-success mb-2 mr-2">Submit</button>
      <button type="reset" class="btn btn-success mb-2">Reset</button>
    </form>
    <transition name="slideUp">
      <div v-show="submitted" v-cloak class="p-3">Your test drive request for {{ product_name }}
        VIN #{{ vin }} has been submitted.
      </div>
    </transition>
  </div>
</template>
<script>
export default {
  props: ['product_name', 'vin'],
  name: 'Form',
  data() {
    return {
      submitted : false,
      name: '',
      email: '',
      phone: '',
      car: this.product_name,
      vinNum: this.vin
    }
  },

  methods: {
    process() {
      this.submitted = true

      setTimeout(() => {
        this.submitted = false
      }, 5000)

      this.name = ''
      this.email = ''
      this.phone = ''
    }
  }
}
</script>
