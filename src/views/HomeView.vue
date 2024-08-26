<template>
  <div class="home">
    <Carousel class="carousel" v-slot="{ currentSlide }">
      <Slide v-for="(slide, index) in carouselSlides" :key="index">
        <div v-show="currentSlide === index + 1" class="slide-info">
          <img :src="`/${slide}.jpeg`" alt="">
        </div>
      </Slide>
    </Carousel>
  </div>
</template>

<script setup lang="ts">
import Carousel from '../components/Carousel.vue'
import Slide from '../components/Slide.vue'

const carouselSlides = ['bg-1', 'bg-2', 'bg-3']
</script>

<style scoped>
.carousel {
  position: relative;
  max-height: 100vh;
  height: 100vh;
}

.carousel .slide-info {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  max-height: 100%;
  max-width: 100vw;
  height: 100%;
}

.carousel .slide-info img {
  min-width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
