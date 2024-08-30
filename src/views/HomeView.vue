<template>
  <div class="home">
    <img
      src="/bg-home.jpeg"
      alt=""
    />
    <p class="text-box">1 år med dig</p>
  </div>
  <div class="body">
    <div
      class="gift-container"
      :class="{ active: hasOpenedGiftBox }"
    >
      <div
        class="shadow"
        :class="{ active: hasOpenedGiftBox }"
      ></div>
      <div
        class="gift-box"
        :class="{ active: hasOpenedGiftBox }"
      >
        <div
          @click="openGiftBox"
          class="click"
          :class="{ active: hasOpenedGiftBox }"
        ></div>
      </div>
      <div
        class="text"
        :class="{ active: hasOpenedGiftBox, active2: !hasOpenedGiftBox }"
      >
        <button
          @click="goToCarousel"
          class="start-slide"
        >
          Påbörja Resan
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
  import router from '@/router'
  import { ref } from 'vue'

  const hasOpenedGiftBox = ref(false)

  function openGiftBox() {
    hasOpenedGiftBox.value = !hasOpenedGiftBox.value
  }

  function goToCarousel() {
    router.push('/carousel')
  }
</script>

<style scoped lang="scss">
  .home {
    position: relative;
    max-height: 100vh;
    height: 98vh;
  }

  img {
    min-width: 100%;
    height: 100%;
    width: 98vw;
    object-fit: contain;
    user-select: none;
    background: rgb(172, 109, 109);
  }

  .text-box {
    color: white;
    position: absolute;
    font-size: 8rem;
    top: 10px;
    left: calc(50% - 23rem);
    background-color: rgb(212, 172, 172);
    text-align: center;
    padding: 2rem;
    border-radius: 20px;
  }

  .start-slide {
    background-color: rgb(218, 66, 66);
    color: white;
    border-radius: 20px;
    font-weight: bold;
    font-size: 18px;
    font-family: monospace;
    padding: 20px;
    cursor: pointer;
  }

  .start-slide:hover {
    background-color: rgb(211, 102, 102);
  }

  .body {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #25252b;
  }

  .gift-container {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    bottom: 20%;
  }

  .gift-container.active {
    animation: Vibration 1s ease forwards;
  }

  @keyframes Vibration {
    0% {
      transform: scale(1, 1);
    }

    25% {
      transform: scale(0.95, 1.05);
    }

    50% {
      transform: scale(1, 1, 0.9);
    }

    70% {
      transform: scale(0.9, 1.1);
    }

    100% {
      transform: scale(1, 1);
    }
  }

  .gift-container .gift-box {
    position: absolute;
    height: 200px;
    width: 300px;
    background: #ec9c46;
    animation: Bounce 4s ease infinite forwards;
  }

  @keyframes Bounce {
    0% {
      transform: translateY(-24px);
    }

    50% {
      transform: translateY(0px);
    }

    100% {
      transform: translateY(-24px);
    }
  }

  .gift-box.active {
    animation: none;
  }

  .gift-box::before {
    content: '';
    position: absolute;
    width: 50px;
    height: 200px;
    background: #e76f51;
    left: 124px;
  }

  .gift-box::after {
    content: '';
    position: absolute;
    box-shadow: inset 0 10px rgba(0, 0, 0, 0.3);
    width: 300px;
    height: 200px;
  }

  .click {
    position: absolute;
    background: #ec9c4a;
    width: 340px;
    height: 90px;
    top: -90px;
    left: -20px;
    cursor: pointer;
    z-index: 1;
    transition: 0.5s ease;
  }

  .click.active {
    transition-delay: 1s;
    transform: translateY(-240px);
  }

  .click::before {
    content: '';
    position: absolute;
    width: 50px;
    height: 90px;
    background: #e76f51;
    left: 144px;
    z-index: 2;
  }

  .click::after {
    content: '';
    position: absolute;
    width: 5px;
    height: 0;
    border-bottom: 60px solid #e76f51;
    border-top: 60px solid #e76f51;
    border-left: 0px solid transparent;
    border-right: 60px solid transparent;
    transform: rotate(-90deg);
    top: -93px;
    left: 136px;
    z-index: 3;
  }

  .gift-container .shadow {
    content: '';
    position: relative;
    width: 340px;
    height: 40px;
    background: rgba(0, 0, 0.4);
    top: 100px;
    border-radius: 50%;
    left: -4px;
    animation: BounceOut 4s ease infinite forwards;
  }

  .gift-container .shadow.active {
    animation: none;
  }

  @keyframes BounceOut {
    0% {
      transform: translateY(24px);
      scale: 0.7;
    }

    50% {
      transform: translateY(0px);
      scale: 1;
    }

    100% {
      transform: translateY(24px);
      scale: 0.7;
    }
  }

  .text {
    position: absolute;
    background: #ec9c4a;
    text-align: center;
    font-size: 20px;
    color: #e76f51;
    border-radius: 20px;
    z-index: -1;
    transition: 0.5s ease;
    transition-delay: 1.2s;
  }

  .text.active {
    scale: 1;
    transform: translateY(-240px);
  }

  .text.active2 {
    top: 0;
    transition-delay: 0.2s;
  }
</style>
