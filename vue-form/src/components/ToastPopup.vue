<template>
  <div class="toast" v-bind:class="{'animation':open}">로그인이 완료되었습니다.</div>
</template>

<script>
let timer;
export default {
  props: ["open"],
  watch: {
    open(newValue, oldValue) {
      // open이라는 props속성이 바뀔 때마다 동작
      if (newValue) {
        console.log("토스트 팝업 열기");
        clearTimeout(timer);
        timer = setTimeout(() => {
          this.$emit("close");
        }, 2000);
      }
    },
  },
};
</script>

<style scoped>
/* scoped: 현재 컴포넌트에 한해서만 스타일을 적용한다는 의미 */
.toast {
  /* 다른 컴포넌트의 toast클래스는 영향을 주지 않을 것임 */
  width: 200px;
  height: 40px;
  background-color: black;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  bottom: -20%;
  left: 5%;
  transition: bottom 0.2s ease-in-out;
}

.animation {
  bottom: 5%;
}
</style>