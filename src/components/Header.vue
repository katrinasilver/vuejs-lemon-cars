<template>
  <header class="navbar navbar-expand-lg d-flex justify-content-between">
    <div class="d-flex align-items-center">
      <router-link class="navbar-brand" to="/"><h2 class="mb-0 text-warning">Lemon Autos</h2></router-link>
      <p class="mb-0 lead border-left border-muted text-white pl-3">Selling your Dream Car at a sketchy lot nearby</p>
    </div>
  </header>
</template>

<script>

export default {
  name: 'Header'
}
</script>

<style lang="scss">
header.navbar {
  background: #252525;
}
</style>
