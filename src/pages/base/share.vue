<template>
  <div class="share-container">
    <div class="share-item my-share">
      <div class="title">我的分享</div>
      <div class="box">
        <div class="no-data">今天还没有分享噢~</div>
      </div>
    </div>
    <div class="share-item">
      <div class="title">TA的分享</div>
      <div class="box">
        <div class="no-data">
          没有分享记录，先搜一个吧~
        </div>
        <text class="search-icon fa fa-search"></text>
      </div>
    </div>
    <div class="search-content">
      <span class="dot dot1" style="left: 20%; top: 16%;"></span>
      <span class="dot dot2" style="left: 80%; top: 45%;"></span>
      <span class="dot dot3" style="left: 40%; top: 75%;"></span>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {}
  }
}
</script>

<style lang="less">
.share-container {
  padding: 40rpx 64rpx;
}
.share-item {
  margin-bottom: 40rpx;
  .title {
    font-size: 24rpx;
    color: #aaa;
  }
  .box {
    position: relative;
    margin-top: 20rpx;
    padding: 16rpx;
    border-radius: 8rpx;
    box-shadow: 2rpx 2rpx 6rpx rgba(0,0,0,0.2);
    background-color: #fff;
    .search-icon {
      position: absolute;
      right: 62rpx;
      top: 34rpx;
      font-size: 40rpx;
      color: #888;
    }
  }
  .no-data {
    padding: 24rpx;
    text-align: center;
    font-size: 24rpx;
    color: #ccc;
  }
}
.search-content {
  position: relative;
  margin-top: 60rpx;
  height: 500rpx;
  .dot {
    position: absolute;
    width: 30rpx;
    height: 30rpx;
    border-radius: 50%;
    background-color: #2d8cf0;
    overflow: hidden;
    opacity: 0;

    animation: dot 3s linear;
    animation-iteration-count: infinite;
    &.dot1 {
      animation-delay: 0;
    }
    &.dot2 {
      animation-delay: 1s;
    }
    &.dot3 {
      animation-delay: 2s;
    }
  }
}
@keyframes dot {
  0% {
    transform: scale(1);
    opacity: 0;
  }
  2% {
    transform: scale(1);
    opacity: 0.8;
  }
  40% {
    transform: scale(3);
    opacity: 0;
  }
  100% {
    transform: scale(3);
    opacity: 0;
  }
}
</style>

