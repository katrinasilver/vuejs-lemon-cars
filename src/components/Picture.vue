<template>
  <transition name="slideRight">
    <picture v-cloak>
      <img :src="main_img" :alt="product_name" class="img-fluid img-thumbnail mr-2" >
      <img v-for="(img, index) in product_imgs" :key="index"
      class="img-fluid img-thumbnail mr-2"
      :src="product_imgs[index]" :alt="product_name + index">
    </picture>
  </transition>
</template>

<script>
export default {
  props: ['main_img', 'product_name', 'product_imgs'],
  name: 'Picture'
}
</script>

<style lang="scss" scoped>

  .img-thumbnail {
    height: 100%;
    max-width: 100px;
    width: 100%;
  }

</style>
