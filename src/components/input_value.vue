<template>
  <div class="input-number">
    <input type="number" v-bind:value="currentValue" @change="handleChange" @keyup="handleChange"/>
    <button @click="handleDown" :disabled="currentValue<=min">-</button>
    <button @click="handleUp" :disabled="currentValue>=max">+</button>
    <input type="number" :value="currentValue1" @change="handleChange1" @keyup="handleChange1">
  </div>
</template>

<script>
export default {
  name: 'input_value',
  props: {
    value: {
      type: Number,
      default: 0
    },
    max: {
      type: Number,
      default: Infinity
    },
    min: {
      type: Number,
      default: -Infinity
    }
  },
  data () {
    return {
      currentValue: this.value,
      currentValue1: 1
    }
  },
  watch: {
    currentValue: function (val) {
      this.$emit('input', val)
    },
    value: function (val, val1) {
      console.log(val, val1)
      this.updateValue(val)
    }
  },
  methods: {
    handleDown: function () {
      if (this.currentValue < this.min) { return }
      this.currentValue -= this.currentValue1
    },
    handleUp: function () {
      if (this.currentValue > this.max) { return }
      this.currentValue += this.currentValue1
    },
    updateValue: function (val) {
      if (this.max < val) val = this.max
      if (this.min > val) val = this.min
      this.currentValue = val
    },
    handleChange: function (event) {
      console.log(event)
      var val = Number(event.target.value)
      var min = this.min
      var max = this.max
      if (val > max) {
        this.currentValue = max
      } else if (val < min) {
        this.currentValue = min
      } else if (min <= val && val <= max) {
        this.currentValue = val
      }
    },
    handleChange1: function (event) {
      this.currentValue1 = Number(event.target.value)
    }
  },
  mounted: function () {
    this.updateValue(this.value)
  }
}
</script>

<style scoped>

</style>
