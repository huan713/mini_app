<template>
  <div class="container" @click="clickHandle('test click', $event)">

    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
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
      footerItems: [
        {label: 'Write', icon: 'fa-pencil', url: '/pages/write/main'},
        {label: 'Read', icon: 'fa-envelope-open-o'},
        {label: 'Me', icon: 'fa-user-o'}
      ]
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
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 108rpx;
  height: 108rpx;
  margin: 20rpx;
  border-radius: 50%;
}

</style>
