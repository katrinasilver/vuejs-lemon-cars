<template>
  <div id="app" class="bg-light">
    <Header />
    <router-view />
    <footer class="bg-dark text-muted p-4 text-center">&copy; 2019 Lemon Autos // Our cars are more than just lemons!</footer>
  </div>
</template>

<script>
  import Header from '@/components/Header'

  export default {
    name: 'lemon-autos',

    components: {
      Header
    }
  }
</script>

<style lang="scss">
  @import '../node_modules/bootstrap/scss/bootstrap.scss';
  @import '../sass/custom.scss';

  [v-cloak] {
    display: none;
  }

  body {
    text-rendering: optimizeLegibility;
  }

  .slideUp-enter,
  .slideUp-leave-to {
    transform: translateY(100px) rotate(0deg);
    opacity: 0;
  }

  .slideUp-enter-active,
  .slideUp-leave-active {
    transition: all .3s ease;
  }

  .slideRight-leave-to,
  .slideRight-enter {
    transform: translateX(100px) rotate(0deg);
    opacity: 0;
  }

  .slideRight-enter-active,
  .slideRight-leave-active {
    transition: all .3s ease;
  }

</style>
