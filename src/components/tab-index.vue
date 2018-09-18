<template>
    <div v-cloak>
      <tabs v-model="activeKey">
        <pane label="标签1" name="1">
          <p>
            标签1的内容
          </p>
        </pane>
        <pane label="标签2" name="2">
          <p>
            标签2的内容
          </p>
        </pane>
        <pane label="标签3" name="3">
          <p>
            标签3的内容
          </p>
        </pane>
      </tabs>
    </div>
</template>

<script>
import tabs from './tab'
import pane from './pane'
export default {
  name: 'tab-index',
  components: {
    tabs,
    pane
  },
  data () {
    return {
      activeKey: '1'
    }
  }
}
</script>

<style scoped>

</style>
