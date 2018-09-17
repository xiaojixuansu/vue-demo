<template>
  <div>
    <button v-on:click="increaseCnt" style="background: aquamarine">+1</button>
    <button v-on:click="reduceCnt" style="background: aquamarine">-1</button>
    <component4></component4>
    <slot name="lilan">
      <div style="width: 100px;height: 100px;border: 1px dotted">
        <p>nihao</p>
      </div>
    </slot>
    <slot name="mingling">
      <input type="text"/>
    </slot>
  </div>
</template>

<script>
import component4 from './Component4'
let x = 2

export default {
  name: 'component2',
  data () {
    return {
      count: 0
    }
  },
  components: {
    component4
  },
  methods: {
    increaseCnt: function () {
      this.count++
      this.display1(this.count)
      this.$emit('increase', this.count, x)
    },
    reduceCnt: function () {
      this.count--
      this.display1(this.count)
      this.$emit('reduce', this.count, x)
    },
    display1: function (index) {
      console.log(index)
    }
  },
  mounted () {
    console.log(this.$slots)
  }
}
</script>

<style scoped>

</style>
