<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @click="emitCloseModal">닫기</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

// props 정의
const props = defineProps({
  data: Array,
  isModal: Boolean,
  selectedMovie: Number
})

// emit 정의
const emit = defineEmits(['closeModal'])

// 모달 닫기 이벤트 발생 함수
const emitCloseModal = () => {
  emit('closeModal')
}
</script>

<style>
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
  padding: 20px;
  border-radius: 10px;
  text-align: center;
}
</style>
