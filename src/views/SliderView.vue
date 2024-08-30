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
          <img
            :src="`/${slide.image}.jpeg`"
            :class="`${slide.image}`"
          />
          <div class="text">
            <p class="text-box">
              {{ slide.text }}
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
  const carouselSlides = [
    {
      image: 'bg-1',
      text: 'Vi har haft en väldigt intressant år tillsammans, känns som vi har gjort så mycket och hunnit med en massa, som tex...'
    },
    {
      image: 'bg-2',
      text: 'Tyskland med Ebba och Adam! Det var så mysigt att va där i snön med dig, och jag är taggad på ifall vi skulle åka tillbaks...'
    },
    {
      image: 'bg-3',
      text: 'Flytt till nya fina lägenheten! Den är den bästa lägenhet jag har sett, och jag älskar att bo här tillsammans med dig...'
    },
    {
      image: 'bg-4',
      text: 'Jul i Vendel! Mysig stämning och god mat, och speciellt mysigt i bastun med snön runtom, och att rulla oss nakna i snön var så kul...'
    },
    {
      image: 'bg-5',
      text: 'Massa hemmamys! Helt enkelt bara en fantastisk vardag med dig, och allt ditt sass och jävlande (som jag älskar btw)...'
    },
    {
      image: 'bg-6',
      text: 'Hven! Bästa iden nånsin att hyra golfbil, och så mysigt i regnet! Och dom där våfflorna... Mums!'
    },
    {
      image: 'bg-7',
      text: 'Pink! Mycket folk, men så cool livespelning! Och det var skitroligt att vara där med dig...'
    },
    {
      image: 'bg-8',
      text: 'Och framför oss har vi så mycket mer, få julpynta och baka tillsammans i fina lägenheten, och så många fler saker...'
    },
    {
      image: 'bg-9',
      text: 'Och jag kan inte säga att jag vet vad som kommer hända eller vad vi kommer hitta på resten av livet (fast jag är säker på ett par saker)...'
    },
    {
      image: 'bg-10',
      text: 'Men vad jag kan säga med absolut säkerhet, är jag ser fram emot så mycket att spendera varje dag med dig, min älskade lilla tösabit, i alla våra år framåt. Älskar dig <3'
    }
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
        width: 98vw;
        object-fit: contain;
        user-select: none;
        background: rgb(172, 109, 109);
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
        color: white;
        background: inherit;
        overflow: hidden;
        filter: grayscale(5) contrast(9) drop-shadow(0.05em 0.05em black);
        word-wrap: break-word;
        white-space: wrap;
        font-size: 2.5rem;
        user-select: none;
        margin: 0 auto;
        letter-spacing: 0.15em;
        animation: easeText 0.7s steps(50, end);
        animation-fill-mode: forwards;
      }

      @keyframes easeText {
        0% {
          opacity: 0;
        }

        100% {
          opacity: 1;
        }
      }
    }
  }
</style>
