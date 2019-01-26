<template>
  <div class="jumbotron text-white" :style="{'background-image': `url('${main_img}')`}">
    <div v-cloak class="meta p-4 mt-5">
      <h1 class="display-4">{{ product_name }}</h1>
      <h3>{{ tag_line }}</h3>
      <hr>
      <p class="lead content">{{ description.slice(0, 100) }}...</p>
      <router-link class="btn btn-success btn-lg" :to="{ name: 'cars', params: { id, vin } }">Learn More</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Jumbotron',
  props: {
    id: Number,
    product_name : String,
    main_img : String,
    description: String,
    tag_line : String,
    vin: String
  }
}
</script>

<style lang="scss">

.jumbotron {
  background-size: cover;
  background-position: center;
  border-radius: 0;
  height: fill-available;

  @media only screen and (min-width: 575px) {
    height: 750px;
    margin-top: -4rem;
  }

  .meta {
    background: transparentize(#000000, .5);

    @media only screen and (min-width: 960px) {
      max-width: 45%;
    }
  }

  hr {
    background: #ffff;
  }
}

</style>
