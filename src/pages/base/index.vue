<template>
  <div>
    <div class="base-container" :style="{width: bgWidth, height: bgHeight}">
      <div class="container-item share">
        <share></share>
      </div>
      <div class="container-item mine"></div>
    </div>
    <wx-footer :items="items"></wx-footer>
  </div>
</template>

<script>
import WxFooter from '@/components/WxFooter'
import share from './share'
export default {
  data () {
    return {
      bgHeight: '',
      bgWidth: ''
    }
  },
  components: { WxFooter, share },
  mounted () {
    this.getSize()
  },
  methods: {
    getSize () {
      wx.getSystemInfo({
        success: ({windowWidth, windowHeight}) => {
          this.bgHeight = windowHeight + 'px'
          this.bgWidth = windowWidth + 'px'
        }
      })
    }
  }
}
</script>

<style lang="less">
.base-container {
  background-color: #f5f5f5;
}
</style>

