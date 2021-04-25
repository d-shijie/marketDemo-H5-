<template>
  <Swiper>
    <SwiperItem v-for="(item,index) in banners" :key="index">
      <a :href="item.link">
        <img :src="item.image" alt="" @load="imgLoad">
      </a>
    </SwiperItem>
  </Swiper>
</template>

<script>
import Swiper from "@/components/common/swper/Swiper";
import SwiperItem from "@/components/common/swper/SwiperItem";
export default {
  name: "HomeSwiper",
  data(){
    return{

    }
  },
  components:{
    SwiperItem,
    Swiper
  },
  props:{
    banners:{
      type:Array,
      default(){
        return []
      }
    }
  },
  methods:{
    imgLoad(){
      this.$emit("SwiperImageLoad")
    }
  }

}
</script>

<style scoped>

</style>
