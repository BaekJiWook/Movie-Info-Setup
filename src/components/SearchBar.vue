<template>
  <div class="search-box">
    <input
      type="search"
      @change="
        emitSearchMovie($event.target.value);
        inputText.value = $event.target.value;
        $event.target.value = ''
      "
      placeholder="검색어 입력"
    >
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>

<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue'

// props 및 emits 정의
const props = defineProps({
  data: Array,
})

const emit = defineEmits(['searchMovie'])

// 반응형 변수 설정
const inputText = ref('')

// 메서드 정의
const emitSearchMovie = (title) => {
  emit('searchMovie', title)
}

// watch로 inputText 값 변화 감지
watch(inputText, (newValue) => {
  // 입력한 영화제목이 데이터에 있는지 확인
  const findName = props.data.filter(movie => movie.title.includes(newValue))

  if (findName.length === 0) {
    alert('해당하는 자료가 없습니다')
  }
})
</script>

<style>
.search-box {
  padding: 10px;
  display: flex;
  justify-content: center;
}

.search-box input {
  padding: 5px 10px;
}

.search-box button {
  margin: 0;
}
</style>
