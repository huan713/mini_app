<template>
  <div class="wx-footer">
    <div class="wx-footer-item active" :class="{active: activeItem === index}">
      <text class="fa wx-footer-icon fa-heartbeat"></text>
      <span class="wx-footer-text">分享</span>
    </div>
    <div class="wx-footer-item" :class="{active: activeItem === index}">
      <text class="fa wx-footer-icon fa-user"></text>
      <span class="wx-footer-text">我的</span>
    </div>
    <div class="wx-footer-main">
      <div class="text">
        +
      </div>
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
  methods: {}
}
</script>

<style lang="less">
.wx-footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  padding: 16rpx 0;
  border-top: 1px solid #ddd;
  color: #8c8c8c;
  background-color: #f0f0f0;
  &-item {
    display: inline-block;
    width: 43%;
    text-align: center;
    font-size: 20rpx;
    &.active {
      color: #2d8cf0;
    }
  }
  &-item + &-item {
    margin-left: 100rpx;
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
  &-main {
    position: absolute;
    bottom: 28rpx;
    left: 50%;
    margin-left: -50rpx;
    width: 100rpx;
    height: 100rpx;
    border-radius: 50%;
    text-align: center;
    background: linear-gradient(#66bEFF, #0066ee);
    .text {
      width: 86rpx;
      height: 86rpx;
      line-height: 78rpx;
      margin: 5rpx auto;
      border: 4rpx solid rgba(255,255,255,0.8);
      border-radius: 50%;
      color: #fff;
      font-size: 48rpx;
    }
  }
}
</style>

