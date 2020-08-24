<template>
  <div class="toast">토스트 팝업입니다.</div>
</template>

<script>
export default {};
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
  bottom: 5%;
  left: 5%;
}
</style>