<template>
  <div class="search">
    <form class="form-inline">
      <input id="findCar" class="form-control mr-sm-2" type="search" placeholder="Find the car of your fever dreams...">
    </form>
  </div>
</template>

<script>
export default {
  name: 'Search',
}
</script>

<style lang="scss" scoped>

.search {
  .form-control {
    min-width: 300px;
  }
}

</style>
