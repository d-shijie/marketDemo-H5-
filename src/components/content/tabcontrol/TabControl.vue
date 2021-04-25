<template>
  <div class="tab-control">
    <div @click="itemClick(index)" v-for="(item,index) in titles" class="tab-control-item">
      <span :class="{active:currentIndex===index}">{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  props:{
    titles:{
      type:Array,
      default:[]
    }
  },
  data(){
    return {
      currentIndex:0
    }
  },
  methods:{
    itemClick(index){
      this.currentIndex=index
      this.$emit("itemClick",index)
    }
  }
}
</script>

<style scoped>
.tab-control {
  display: flex;
}
.tab-control-item {
  flex: 1;
  text-align: center;
}
span {
  padding: 4px 7px;

}
.active {
  border-bottom: 2px solid #ea0000;
  color: #ee0000;
}
</style>