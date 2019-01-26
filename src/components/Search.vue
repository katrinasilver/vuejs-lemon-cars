<template>
  <div class="search center border pt-3 pb-3">
    <form class="form-inline d-flex justify-content-center my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Find the car of your fever dreams...">
      <button class="btn btn-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Search'
}
</script>

<style lang="scss">
.search {

  .form-control {
    width: 65%;
  }
}
</style>
