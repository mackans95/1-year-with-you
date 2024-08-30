<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="carousel">
    <slot :current-slide="currentSlide" />

    <!-- Navigation -->
    <div class="navigate">
      <div
        v-if="currentSlide > 1"
        class="toggle-page left"
      >
        <i
          @click="prevSlide"
          class="fas fa-chevron-left"
        />
      </div>
      <div
        v-if="currentSlide !== getSlideCount"
        class="toggle-page right"
      >
        <i
          @click="nextSlide"
          class="fas fa-chevron-right"
        />
      </div>
    </div>

    <!-- Pagination -->
    <div class="pagination">
      <span
        v-for="(_, index) in getSlideCount"
        :key="index"
        :class="{ active: index + 1 === currentSlide }"
        @click="goToSlide(index)"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
  // -- IMPORTS --
  import { ref, onMounted } from 'vue'

  // -- VARIABLES --
  const currentSlide = ref(1)
  const getSlideCount = ref<number>()

  // -- LIFECYCLE-HOOKS --
  onMounted(() => {
    getSlideCount.value = document.querySelectorAll('.slide').length
  })

  // -- METHODS --
  function nextSlide() {
    if (currentSlide.value !== getSlideCount.value) currentSlide.value++
  }

  function prevSlide() {
    if (currentSlide.value !== 1) currentSlide.value--
  }

  function goToSlide(index: number) {
    currentSlide.value = index + 1
  }
</script>

<style lang="scss" scoped>
  .navigate {
    height: 100%;
    width: 100%;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;

    .toggle-page {
      display: flex;
      flex: 1;
    }

    .right {
      justify-content: flex-end;
    }

    i {
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      background-color: #6347c7;
      color: #fff;
    }
  }

  .pagination {
    position: absolute;
    bottom: 24px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 16px;

    span {
      cursor: pointer;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      background-color: #fff;
      box-shadow:
        0 1px 3px 0 rgba(0, 0, 0, 0.1),
        0 1px 2px 0 rgba(0, 0, 0, 0.06);
    }

    .active {
      background-color: #6347c7;
    }
  }
</style>
