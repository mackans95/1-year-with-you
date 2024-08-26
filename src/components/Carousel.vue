<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="carousel">
    <slot :current-slide="currentSlide" />

    <!-- Navigation -->
    <div class="navigate">
      <div class="toggle-page left">
        <i @click="prevSlide" class="fas fa-chevron-left"></i>
      </div>
      <div class="toggle-page right">
        <i @click="nextSlide" class="fas fa-chevron-right"></i>
      </div>
    </div>

    <!-- Pagination -->
    <div class="pagination">
      <span v-for="(slide, index) in getSlideCount" @click="goToSlide(index)" :key="index"
        :class="{ active: index + 1 === currentSlide }">
      </span>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'

const currentSlide = ref(1)
const getSlideCount = ref<number>()

// next slide
function nextSlide() {
  if (currentSlide.value === getSlideCount.value) {
    currentSlide.value = 1
    return
  }

  currentSlide.value += 1
}

// prev slide
function prevSlide() {
  if (currentSlide.value === 1) {
    currentSlide.value = 1
    return
  }

  currentSlide.value -= 1
}

function goToSlide(index: number) {
  currentSlide.value = index + 1
}

onMounted(() => {
  getSlideCount.value = document.querySelectorAll('.slide').length
})
</script>

<style scoped>
.navigate {
  height: 100%;
  width: 100%;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
}

.navigate .toggle-page {
  display: flex;
  flex: 1;
}

.navigate .right {
  justify-content: flex-end;
}

.navigate i {
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

.pagination {
  position: absolute;
  bottom: 24px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;
}

.pagination span {
  cursor: pointer;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #fff;
  box-shadow:
    0 1px 3px 0 rgba(0, 0, 0, 0.1),
    0 1px 2px 0 rgba(0, 0, 0, 0.06);
}

.pagination .active {
  background-color: #6347c7;
}
</style>
