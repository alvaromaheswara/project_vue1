<template>
    <div class="carousel">
      <vue-carousel>
        <slide v-for="(image, index) in images" :key="index">
          <img :src="image" alt="carousel image" />
        </slide>
      </vue-carousel>
    </div>
  </template>
  
  <script>
  import { VueCarousel, Slide } from 'vue-carousel';
  
  export default {
    components: {
      VueCarousel,
      Slide
    },
    props: {
      images: Array
    }
  };
  </script>
  
  <style scoped>
  .carousel {
    width: 80%;
    margin: auto;
  }
  
  img {
    width: 100%;
    height: auto;
  }
  </style>
  