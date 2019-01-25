<template>
  <div class="jumbotron text-white" :style="{'background-image': `url('${main_img}')`}">
    <div class="meta p-4 mt-5">
      <h1 class="display-4">{{ product_name }}</h1>
      <h3>{{ tag_line }}</h3>
      <hr>
      <p class="lead content">{{ description.slice(0, 200) }}...</p>
      <a class="btn btn-success btn-lg" role="button">Learn more</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Jumbotron',
  props: {
    product_name : String,
    main_img : String,
    description: String,
    tag_line : String
  }
}
</script>

<style lang="scss">
.jumbotron {
  background-size: cover;
  background-position: center;
  height: fill-available;
  margin-top: -4rem;

  .meta {
    background: transparentize(#000000, .5);
    max-width: 45%;
  }

  hr {
    background: #ffff;
  }
}
</style>
