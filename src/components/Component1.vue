<template>
  <div>
    {{messages}}
    <button @click="cnt++">{{cnt}}</button>
    <div v-bind:style="{'fontSize':question1+'px','border':'1px solid #ddd'}">nihao</div>
    <div style="width: 100px;border:1px solid #ff0000">
      <li v-for="(value,index) in question2" v-bind:key="index">
        <a>{{value.data}}:{{value.name}}</a>
      </li>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'component1',
  data(){
    return{
      messages:"nihao23",
      cnt:this.question1
    }
  },
  // props:["question1","question2"]
  props:{
    question1:Number,
    question2:{
      type:Array,
      default(){
        return []
      }
    }
  }
}
</script>

<style scoped>

</style>
