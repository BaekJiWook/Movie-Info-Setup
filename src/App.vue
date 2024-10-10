<template>
  <Navbar />
  <Event :text="text[eventTextNum]" />
  <SearchBar 
    :data="dataTemp" 
    @searchMovie="searchMovie"
  />
  
  <p>
    <button @click="showAllMovie" class="btn-all">전체보기</button>
  </p>
  <Movies 
    :data="dataTemp" 
    @openModal="openModal" 
    @increseLike="increseLike" 
  />  

  <Modal 
    :data="data"
    :isModal="isModal"
    :selectedMovie="selectedMovie"
    @closeModal="closeModal"
  />
</template>

<script setup>
import { ref } from 'vue'
import data from './assets/movies'
import Navbar from './components/Navbar.vue'
import Modal from './components/Modal.vue'
import Event from './components/Event.vue'
import Movies from './components/Movies.vue'
import SearchBar from './components/SearchBar.vue'

// 반응형 데이터 및 상태 관리
const isModal = ref(false)
const dataTemp = ref([...data])  // 원본 데이터와 동일한 사본 데이터 생성
const selectedMovie = ref(0)
const text = ref([
  'NETPLIX 강렬한 운명의 드라마, 경기크리처',
  '디즈니 100주년 기념작, 위시',
  '그날, 대한민국의 운명이 바뀌었다, 서울의 봄',
])
const eventTextNum = ref(0)

// 좋아요 수 증가 함수 (부모 컴포넌트에서 데이터 수정)
const increseLike = (id) => {
  const movie = dataTemp.value.find(movie => movie.id === id)
  if (movie) {
    movie.like += 1
  }
}

// 검색 기능 구현
const searchMovie = (title) => {
  dataTemp.value = data.filter(movie => movie.title.includes(title))
}

// 모든 영화 보기
const showAllMovie = () => {
  dataTemp.value = [...data]
}

// 모달 열기 및 닫기 기능
const openModal = (movieId) => {
  selectedMovie.value = movieId
  isModal.value = true
}

const closeModal = () => {
  isModal.value = false
}
</script>

<style>
/* 스타일 설정 */
.container {
  padding: 20px;
}

.center {
  text-align: center;
}

button {
  margin-right: 10px;
  margin-top: 1rem;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}

.modal {
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
