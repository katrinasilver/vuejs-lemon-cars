<template>
  <form class="test-drive mt-4 was-validated">
    <div class="form-group">
      <label for="name">Your Name</label>
      <input type="text" class="form-control" id="name" placeholder="enter your full name" required autofocus>
    </div>
    <div class="form-group">
      <label for="email">Email</label>
      <input type="email" class="form-control" id="email" placeholder="your@example.com" required>
    </div>
    <div class="form-group">
      <label for="phone">Phone</label>
      <input type="tel" class="form-control" id="phone" placeholder="123-456-7890" required>
    </div>
    <button type="submit" class="btn btn-success mb-2 mr-2">Submit</button>
    <button type="reset" class="btn btn-success mb-2">Reset</button>
  </form>
</template>
<script>
export default {
  props: ['product_name', 'vin'],
  name: 'Form'
}
</script>
