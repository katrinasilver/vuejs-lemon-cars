<template>
  <header class="navbar navbar-expand-lg navbar-dark">
    <router-link class="navbar-brand" to="/"><h3 class="mb-0">Lemon Autos</h3></router-link>
    <p class="text-white mb-0 lead border-left border-white pl-3">Selling your Dream Car at a sketchy lot nearby</p>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="scss" scoped>
header.navbar {
  background: #25292e;

  @media only screen and (min-width: 575px) {
    background: transparentize(#25292e, .3);
    z-index: 1000;
  }
}
</style>
