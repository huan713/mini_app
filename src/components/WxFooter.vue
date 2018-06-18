<template>
  <div class="wx-footer">
    <div
      :style="{width: itemWidth}"
      class="wx-footer-item"
      :class="{active: activeItem === index}"
      v-for="(item, index) in items"
      :key="item.label"
      @click="itemClick(index, item.url)">
      <text class="fa wx-footer-icon" :class="item.icon"></text>
      <span class="wx-footer-text">{{item.label}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'WxFooter',
  data () {
    return {
      activeItem: -1
    }
  },
  props: {
    items: Array
  },
  computed: {
    itemWidth () {
      return 100 / this.items.length + '%'
    }
  },
  methods: {
    itemClick (index, url) {
      this.activeItem = index
      if (url) {
        wx.navigateTo({ url })
      }
    }
  }
}
</script>

<style lang="less">
.wx-footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  padding: 16rpx 0;
  border-top: 1px solid #e5e5e5;
  color: #4c4c4c;
  background-color: #f5f5f5;
  &-item {
    float: left;
    text-align: center;
    font-size: 24rpx;
    &.active {
      color: #409EFF;
    }
  }
  &-icon {
    display: block;
    font-size: 40rpx;
  }
  &-text {
    display: block;
    margin-top: 8rpx;
  }
  &::after {
    content: '';
    display: block;
    clear: both;
  }
}
</style>

