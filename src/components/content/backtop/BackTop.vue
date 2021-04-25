<template>
<div class="back-top">
  <img src="../../../assets/img/common/top.png" alt="">
</div>
</template>

<script>
export default {
  name: "BackTop"
}
</script>

<style scoped>
.back-top {
  position: fixed;
  bottom: 50px;
  right: 8px;
  z-index: 99;
}
img {
  width: 45px;
  height: 45px;
}
</style>