<template>
  <div class="event" :class="{show:isOpen}">
  <!-- class="event show클래스를 두개 설정 시 그냥 두개 적으면 된다 
     하지만 상태를 변화시키기 위해 v-bind로 설정할것임-->
  <!-- :class="{show:true}" show라는 클래스는 true일때만 활성화-->
  <!-- 상태변수 값으로 추가할거야(isOpen)-->
    <p>{{ text }}</p>
    <button @click="isOpen=false">X</button>
  </div>
</template>
  
<script>
  export default {
    name: "EventComponent",
    props: {
      text: String,
    },
    data(){
      return{
        isOpen: true,
        // 상태변수 값으로 추가할거야(isOpen)
      }
    }
  }
</script>
  
<style>
  .event {
  background: #444;
  color: #fff;
  padding: 10px 20px;
  text-align: center;
  font-size: small;
  display: flex;
  justify-content: space-between;
  align-items: center;
  display: none;
  /* 이벤트창이 기본값으로 보이지 않게 설정
  _클릭이벤트로 보이게 설정하게 위해 */
}

.show {
  display: flex;
  /* show라는 클래스는 기본적으로 보인다(flex)는 뜻임 */
}

.event p {
  margin: 0;
}

.event button {
  margin: 0;
}
</style>