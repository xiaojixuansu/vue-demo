<template>
  <div class="tab">
    <div class="tabs-bar">
      <div v-for="(item,index) in navList" v-bind:key="item.label"
      :class="tabClass(item)"
      @click="handleChange(index)">
        {{item.label}}
      </div>
      <div class="tabs-tab" @click="addTab">+</div>
    </div>
    <div class="tabs-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import pane from './pane'
export default {
  name: 'tab',
  props: {
    value: {
      type: [String, Number]
    }
  },
  components: {
    pane
  },
  data () {
    return {
      currentValue: this.value,
      navList: []
    }
  },
  methods: {
    tabClass: function (item) {
      return [
        'tabs-tab',
        {
          'tabs-tab-active': item.name === this.currentValue
        }
      ]
    },
    getTabs () {
      // console.log(this.$children)
      return this.$children.filter(function (item) {
        // console.log(item.$options)
        return item.$options.name === 'pane'
      })
    },
    updateNav () {
      this.navList = []
      var _this = this
      this.getTabs().forEach(function (pane, index) {
        _this.navList.push({
          label: pane.label,
          name: pane.name || index
        })
        if (!pane.name) pane.name = index
        if (index === 0) {
          if (!_this.currentValue) {
            _this.currentValue = pane.name || index
          }
        }
      })
      this.updateStatus()
    },
    updateStatus () {
      var tabs = this.getTabs()
      var _this = this
      tabs.forEach(function (tab) {
        console.log(tab, 'nihao')
        if (tab.name === _this.currentValue) {
          tab.show = true
          // let div = document.createElement('div')
          // div.innerHTML = 'nihao'
          // if (tab.label === '标签1') {
          //   tab.$el.appendChild(div)
          // }
        } else { tab.show = false }
      })
    },
    handleChange: function (index) {
      var nav = this.navList[index]
      var name = nav.name
      this.currentValue = name
      this.$emit('input', name)
    },
    addTab: function () {
      let cnt = this.currentValue + 1
      this.currentValue += 1
      this.navList.push({
        label: 'label' + cnt,
        name: cnt
      })
      console.log(this.$children)
      // this.$nextTick(function () {
      //   pane.props.label = 'label' + cnt
      //   pane.props.name = cnt
      //   this.$children.push(pane)
      // })
      let div = document.createElement(pane)
      console.log(div)
    }
  },
  watch: {
    value: function (val) {
      this.currentValue = val
    },
    currentValue: function () {
      this.updateStatus()
    }
  }
}
</script>

<style scoped>

</style>
