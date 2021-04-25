<template>
<div class="home-feature">
  <div v-for="(item,index) in recommend" class="home-feature-item">
  <img  :src="item.image" alt="">
    <div class="title">{{item.title}}</div>
  </div>
</div>
</template>

<script>
export default {
  name: "HomeFeatrue",
  props:{
    recommend:{
      type:Array,
      default() {
        return [];
      }
    }
  }
}
</script>

<style scoped>
.home-feature {
  padding: 15px 0;
  border-bottom: 8px solid #cecece;
  display: flex;
  text-align: center;
  justify-content: space-around;
}
.home-feature-item {
  flex: 1;
}
img {
  width: 70px;
  height: 70px;
}
.title {
  font-size: 12px;
  margin-top: 10px;
}
</style>