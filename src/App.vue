<template>
  <div id="app" class="bg-light">
    <transition :name="transitionName">
      <router-view />
    </transition>
  </div>
</template>

<script>
  export default {
    name: 'lemon-autos',
    data() {
      return {
        transitionName: ''
      }
    },
    watch: {
      '$route' (to, from) {
        const toDepth = to.path.split('/').length
        const fromDepth = from.path.split('/').length
        this.transitionName = toDepth < fromDepth ? 'slideRight' : 'slideUp'
      }
    }
  }
</script>

<style lang="scss">
  @import '../node_modules/bootstrap/scss/bootstrap.scss';
  @import '../sass/custom.scss';

  [v-cloak] {
    opacity: 0;
    transition: all .3s linear;
    visibility: hidden;
  }

  header.navbar {
    background: #252525;

    @media only screen and (min-width: 992px) {
      input {
        width: 60%;
      }
    }
  }

  body {
    text-rendering: optimizeLegibility;
  }

  .slideUp-enter,
  .slideUp-leave-to {
    transform: translateY(100px);
    opacity: 0;
  }

  .slideUp-enter-active,
  .slideUp-leave-active {
    transition: all .3s ease;
  }

  .slideRight-leave-to,
  .slideRight-enter {
    transform: translateX(50px);
    opacity: 0;
  }

  .slideRight-enter-active,
  .slideRight-leave-active {
    transition: all .3s ease;
  }

</style>
