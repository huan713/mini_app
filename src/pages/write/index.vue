<template>
  <div class="write-container">
    <form class="write-form">
      <textarea
        v-model="formData.mood"
        class="write-area"
        bindblur="bindTextAreaBlur"
        maxlength="200"
        auto-focus
        placeholder="记录你现在的心情..."
        placeholder-style="color: #bbb;"/>
      <!-- <visible :show.sync="formData.show"></visible> -->
    </form>
    <footer-submit></footer-submit>
  </div>
</template>

<script>
import Visible from '@/components/visible'
import WxButton from '@/components/WxButton'
import footerSubmit from '@/components/footerSubmit'
export default {
  data () {
    return {
      formData: {
        mood: '',
        show: true
      }
    }
  },
  components: { Visible, WxButton, footerSubmit },
  methods: {
    formSubmit () {
      console.log(this.formData)
    }
  }
}
</script>

<style lang="less">
.write-container {

  .write-form {
    width: 100%;
    padding: 20rpx;
  }
  .write-area {
    width: 90%;
    margin: 0 auto;
    height: 280rpx;
  }
  .write-btns {
    margin-top: 80rpx;
    text-align: center;
  }
}
</style>

