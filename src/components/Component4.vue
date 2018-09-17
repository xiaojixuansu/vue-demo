<template>
  <div>
    <div :style="{'width':width+'px','height':height+'px','background':'#ff0000'}">
    </div>
  </div>
</template>

<script>

import bus from './bus'
export default {
  name: 'component4',
  data () {
    return {
      width: 400,
      height: 400
    }
  },
  mounted () {
    bus.$on('fun', (width, height) => {
      console.log(this.$parent)
      console.log(width)
      this.width = width
      this.height = height
    }
    )
  }
}
</script>

<style scoped>

</style>
