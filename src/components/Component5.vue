<template>
    <div>
      <component3></component3>
      <component2 ref="comA">
        <p slot="lilan">nihaoma</p>
      </component2>
      <button @click="handleref">nihao</button>
      <!--<component5 :cnt1="cnt1+1" v-if="cnt1<3"></component5>-->
      <inputValue v-model="value" :max="1000" :min="0"></inputValue>
    </div>
</template>

<script>

import inputValue from './input_value'
import component3 from './Component3'
import component2 from './Component2'
export default {
  name: 'component5',
  components: {
    component3,
    component2,
    inputValue
  },
  props: {
    cnt1: {
      type: Number,
      default: 1
    }
  },
  data () {
    return {
      message: 'nihao',
      value: 10
    }
  },
  methods: {
    handleref: function () {
      console.log(this.$refs)
    }
  }
}
</script>

<style scoped>

</style>
