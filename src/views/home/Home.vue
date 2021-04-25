<template>
  <div class="home">
    <nav-bar class="nav-bar">
      <div slot="center">蘑菇街</div>
    </nav-bar>
    <scroll class="content" ref="scroll"
            :probe-type="3"
            :pull-up-load="true"
            @pullingUp="ContentPullingUp"
            @scroll="ContentScroll">
      <home-swiper class="home-swiper" :banners="swiperImg" @SwiperImageLoad></home-swiper>
      <home-feature :recommend="feature"></home-feature>
      <home-pop/>
      <tab-control :titles="['流行','新款','精选']"
                   @itemClick="tabClick"></tab-control>
      <Goods :goods="goods[currentType].list"></Goods>
    </scroll>
    <back-top @click.native="BackTop" v-show="isShowBackTop"></back-top>
  </div>
</template>

<script>
import {getHomeData,getHomeGoods} from "@/network/home";
import Scroll from "@/components/common/scroll/Scroll";
import NavBar from "@/components/common/navbar/NavBar";
import HomeSwiper from "@/views/home/childComp/HomeSwiper";
import HomeFeature from "@/views/home/childComp/HomeFeature";
import HomePop from "@/views/home/childComp/HomePop";
import TabControl from "@/components/content/tabcontrol/TabControl";
import Goods from "@/components/content/goods/Goods";
import BackTop from "@/components/content/backtop/BackTop";
export default {
  name: "Home",
  data(){
    return {
      swiperImg:[],//轮播图图片
      feature:[],//推荐图片和title
      goods:{
        "pop":{
          page:0,
          list:[]
        },
        "new":{
          page: 0,
          list: []
        },
        "sell":{
          page:0,
          list:[]
        }
      },//商品信息
      currentType:"pop",//当前的商品种类
      currentPositionY:0//当前的y值
    }
  },
  components:{
    Scroll,
    NavBar,
    HomeSwiper,
    HomeFeature,
    HomePop,
    TabControl,
    Goods,
    BackTop
  },
  computed:{
    //显示返回顶部按钮的条件
    isShowBackTop(){
      return this.currentPositionY>1500? true:false
    }
  },
  methods:{
    //下拉刷新 根据当前商品页也能做出相应刷新
    ContentPullingUp(){
      this.getHomeGoods(this.currentType)
      this.$refs.scroll.finishPullUp()
      this.$refs.scroll.refresh()
    },
    //返回顶部 组件的点击事件要加.active
    BackTop(){
      this.$refs.scroll.scrollTo(0,0,300)
    },
    //得到Y坐标
    ContentScroll(position){
      this.currentPositionY=-position.y
    },
    //商品的图片加载完成就刷新一遍 清楚卡顿 非父子组件通过事件总线 在原型中注册
    GoodsImageLoad(){
      this.$bus.$on("GoodsImageLoad",()=>{
        this.$refs.scroll.refresh()
      })
    },
    //轮播图的图片刷新
    SwiperImageLoad(){
      this.$refs.scroll.refresh()
    },
    //点击选项切换商品种类 根据下标值 子组件传父组件
    tabClick(index){
      switch (index){
        case 0:
          this.currentType="pop"
          break;
        case 1:
          this.currentType="new"
          break;
        case 2:
          this.currentType="sell"
          break;
      }
    },
    //请求的推荐数据和轮播图数据
    getHomeMultidata(){
      getHomeData().then(res=>{
        this.swiperImg=res.data.data.banner.list
        this.feature=res.data.data.recommend.list
      })
    },
    //请求首页商品数据
    getHomeGoods(type){
      const page=this.goods[type].page+1
      getHomeGoods(type,page).then(res=>{
        this.goods[type].list.push(...res.data.data.list)
        this.goods[type].page+=1
      })
    }
  },
  created() {
    this.getHomeMultidata()
    //得到三类商品的数据 有三类 请求三次 每次请求一类
    this.getHomeGoods("pop")
    this.getHomeGoods("new")
    this.getHomeGoods("sell")
  }
}
</script>

<style scoped>
.home {
  height: 100vh;
}
.content {
  margin-top: 44px;
  height: calc(100% - 93px);
}
.nav-bar {
  background-color: #e798a7;
  font-size: 18px;
  color: #ffffff;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1;
}



</style>