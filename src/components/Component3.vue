<template>
  <div>
    <img src="../assets/img01.jpg" :style="{'height':height+'px','width':width+'px'}" >
    <button @click="fun">点击按钮</button>
  </div>
</template>

<script>
import bus from './bus'
/* eslint-disable */
export default {
  name: 'component3',
  data(){
    return {
      width:120,
      height:120
    }
  },
  methods:{
    fun:function () {
      this.width+=20;
      this.height+=20;
      bus.$emit('fun',this.width,this.height);
    }
  }
}
</script>

<style scoped>

</style>

