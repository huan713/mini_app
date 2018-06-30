<template>
  <div class="container index-container" @click="clickHandle('test click', $event)" :style="{width: bgWidth, height: bgHeight}">

    <!-- <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
    </div> -->
    <!-- <img src="../../../static/timg.jpg" class="index-bg" :style="{width: bgWidth, height: bgHeight}"> -->
    <div class="index-theme">
      <div type="text" class="theme-border"></div>
      <span class="theme-badge"></span>
    </div>
    <div class="index-menu">
      <ul>
        <li class="menu-item letter">
          <span class="icon"><i class="fa fa-envelope-open"></i></span>
          <span class="text">发现</span>
        </li>
        <li class="menu-item user">
          <span class="icon"><i class="fa fa-user"></i></span>
          <span class="text">我的</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'
import WxFooter from '@/components/WxFooter'

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {},
      bgWidth: 0,
      bgHeight: 0
    }
  },

  components: {
    card, WxFooter
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    },
    getSize () {
      wx.getSystemInfo({
        success: ({windowWidth, windowHeight}) => {
          this.bgHeight = windowHeight + 'px'
          this.bgWidth = windowWidth + 'px'
        }
      })
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
    this.getSize()
  }
}
</script>

<style lang="less" scoped>
.index-container {
  /* background-image: url('../../../static/timg.jpg'); */
  background-color: black;
  position: relative;
}

.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 108rpx;
  height: 108rpx;
  border-radius: 50%;
}

.index-theme {
  width: 100%;
  position: absolute;
  bottom: 40%;
  .theme-border {
    width: 72%;
    height: 72rpx;
    margin: 0 auto;
    border: 1px solid rgba(255,255,255,0.6);
    border-radius: 16rpx;
  }
  .theme-badge {
    position: absolute;
    bottom: -16rpx;
    right: 120rpx;
    display: block;
    width: 12rpx;
    height: 8rpx;
    border: 6px solid #000;
    border-bottom-left-radius: 200%;
    border-bottom-right-radius: 200%;
    background-color: rgba(200,200,200,0.5);
  }
}

.index-menu {
  position: absolute;
  bottom: 20%;
  width: 100%;
  text-align: center;
  .menu-item {
    display: inline-block;
    margin: 0 80rpx;
    color: #fff;
    opacity: 0.8;
    .icon {
      display: block;
      width: 100rpx;
      height: 100rpx;
      line-height: 90rpx;
      text-align: center;
      border-radius: 50%;
      font-size: 48rpx;
    }
    &.letter .icon {
      background-color: #409EFF;
    }
    &.user .icon {
      background-color: #E6A23C;
    }
    .text {
      display: block;
      margin-top: 16rpx;
      padding-left: 6rpx;
      font-size: 28rpx;
      letter-spacing: 6rpx;
    }
  }
}

</style>
