<template>
  <div class="goods">
    <GoodsItem :goods-item="item" v-for="item in goods">

    </GoodsItem>
  </div>
</template>

<script>
import GoodsItem from "@/components/content/goods/GoodsItem";
export default {
  name: "Goods",
  props:{
    goods:{
      type:Array,
      default(){
        return []
      }
    }
  },
  components:{
    GoodsItem
  }
}
</script>

<style scoped>
.goods {
  margin-top: 10px;
  padding: 3px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>