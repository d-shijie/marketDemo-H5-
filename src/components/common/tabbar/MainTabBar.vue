<template>
<div class="main-tab-bar">
  <TabBar class="tab-bar">
    <TabBarItem class="tab-bar-item" path="/home" active-color="blue">
      <img slot="item-icon" src="../../../assets/img/tabbar/首页1.svg" alt="">
      <img slot="item-active" src="../../../assets/img/tabbar/首页2.svg" alt="">
      <div slot="item-text">首页</div>
    </TabBarItem>
    <TabBarItem path="/category" active-color="blue">
      <img slot="item-icon" src="../../../assets/img/tabbar/1.svg" alt="">
      <img slot="item-active" src="../../../assets/img/tabbar/2.svg" alt="">
      <div slot="item-text">分类</div>
    </TabBarItem>
    <TabBarItem path="/cart" active-color="blue">
      <img slot="item-icon" src="../../../assets/img/tabbar/购物车1.svg" alt="">
      <img slot="item-active" src="../../../assets/img/tabbar/购物车2.svg" alt="">
      <div slot="item-text">购物车</div>
    </TabBarItem>
    <TabBarItem path="profile" active-color="blue">
      <img slot="item-icon" src="../../../assets/img/tabbar/我的1.svg" alt="">
      <img slot="item-active" src="../../../assets/img/tabbar/我的2.svg" alt="">
      <div slot="item-text">我的</div>
    </TabBarItem>
  </TabBar>
</div>
</template>

<script>
import TabBar from "@/components/common/tabbar/TabBar";
import TabBarItem from "@/components/common/tabbar/TabBarItem";
export default {
name: "MainTabBar",
  components:{
  TabBarItem,
    TabBar
  }
}
</script>

<style scoped>
.tab-bar {
  border-top: 1px solid rgba(0,0,0,.3);
  background-color: #f2f2f2;
  text-align: center;
  display: flex;
}
.tab-bar-item{
  flex: 1;
}
.tab-bar-item img {
  width: 28px;
  height: 28px;
}
.main-tab-bar{
  height: 49px;
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
}
</style>