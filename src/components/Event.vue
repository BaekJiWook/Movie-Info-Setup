<template>
  <div class="event">
    <p>{{ text }}</p>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

// props 정의
const props = defineProps({
  text: {
    type: String,
    required: true,
  }
})
</script>

<style>
.event {
  background: #444;
  color: #fff;
  padding: 10px 20px;
  text-align: center;
  font-size: small;
}

.event p {
  margin: 0;
}
</style>
