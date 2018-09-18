<template>
    <div class="pane" v-show="show">
      <slot></slot>
    </div>
</template>

<script>
export default {
  name: 'pane',
  props: {
    name: {
      type: String
    },
    label: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      show: true
    }
  },
  methods: {
    updateNav () {
      console.log(this.$parent)
      this.$parent.updateNav()
    }
  },
  watch: {
    label () {
      this.updateNav()
      let div = document.createElement('div')
      div.innerHTML = '你好'
      console.log(this.$parent)
    }
  },
  mounted () {
    this.updateNav()
  }
}
</script>

<style scoped>

</style>
