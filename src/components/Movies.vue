<template>
  <div class="container">
    <h1>영화정보</h1>
    <div v-for="(movie) in data" :key="movie.id" class="item">
      <figure>
        <!-- 문자열 템플릿 대신 단순한 바인딩 사용 -->
        <img :src="movie.imgUrl" :alt="movie.title">
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button @click="emitIncreseLike(movie.id)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="emitOpenModal(movie.id)">상세보기</button>
        </p>
      </div>
    </div>    
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

// props 정의
const props = defineProps({
  data: {
    type: Array,
    required: true,
  }
})

// emit 정의
const emit = defineEmits(['increseLike', 'openModal'])

// 좋아요 증가 이벤트 발생 함수
const emitIncreseLike = (id) => {
  emit('increseLike', id)
}

// 모달 열기 이벤트 발생 함수
const emitOpenModal = (id) => {
  emit('openModal', id)
}
</script>

<style>
.container {
  padding: 20px;
}

.item {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 20px;
}

.item figure {
  margin: 0;
  padding: 0;
}

.item img {
  max-width: 100%;
  height: auto;
}

.bg-yellow {
  background-color: yellow;
}
</style>
