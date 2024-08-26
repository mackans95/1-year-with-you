<template>
  <div class="home">
    <Carousel
      class="carousel"
      v-slot="{ currentSlide }"
    >
      <Slide
        v-for="(slide, index) in carouselSlides"
        :key="index"
      >
        <div
          v-show="currentSlide === index + 1"
          class="slide-info"
        >
          <img :src="`/${slide}.jpeg`" />
          <div class="text">
            <p class="text-box">
              {{ texts[index] }}
            </p>
          </div>
        </div>
      </Slide>
    </Carousel>
  </div>
</template>

<script setup lang="ts">
  // -- IMPORTS --
  import Carousel from '../components/Carousel.vue'
  import Slide from '../components/Slide.vue'

  // -- VARIABLES --
  const carouselSlides = ['bg-1', 'bg-2', 'bg-3']
  const texts = [
    "Hello this is text number one",
    "This here would be text number 2",
    "And lastly this is the text for image number 3"
  ]
</script>

<style lang="scss" scoped>
  .carousel {
    position: relative;
    max-height: 100vh;
    height: 98vh;

    .slide-info {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      max-height: 100%;
      max-width: 100vw;
      height: 100%;

      img {
        min-width: 100%;
        height: 100%;
        object-fit: cover;
        user-select: none;
      }
    }

    .text {
      display: flex;
      justify-content: center;

      .text-box {
        position: absolute;
        max-width: 35rem;
        top: 10rem;
        right: 5rem;
        left: 60%;
        color: #fff;
        overflow: hidden;
        filter: grayscale(5) contrast(9) drop-shadow(0.05em 0.05em red);
        word-wrap: break-word;
        white-space: wrap;
        font-size: 2.5rem;
        user-select: none;
        margin: 0 auto;
        letter-spacing: 0.15em;
        animation:
          easeText .7s steps(50, end);
        animation-fill-mode: forwards;
      }

      @keyframes easeText {
        0% { opacity: 0;}
        100% { opacity: 1;}
      }
    }
  }
</style>
