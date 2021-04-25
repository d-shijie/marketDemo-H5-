<template>
<div class="tab-bar">
  <slot></slot>
</div>
</template>

<script>
export default {
name: "TabBar"
}
</script>

<style scoped>
.tab-bar {
  height: 49px;
}
</style>