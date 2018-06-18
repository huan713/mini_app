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
      <visible :show.sync="formData.show"></visible>
      <div class="write-btns">
        <wx-button @click="formSubmit" type="info">提交</wx-button>
      </div>
    </form>
  </div>
</template>

<script>
import Visible from '@/components/visible'
import WxButton from '@/components/WxButton'
export default {
  data () {
    return {
      formData: {
        mood: '',
        show: true
      }
    }
  },
  components: { Visible, WxButton },
  methods: {
    formSubmit () {
      console.log(this.formData)
    }
  }
}
</script>

<style lang="less">
.write-container {
  width: 90%;
  margin: 40rpx auto;

  .write-form {
    width: 100%;
  }
  .write-area {
    height: 280rpx;
  }
  .write-btns {
    margin-top: 80rpx;
    text-align: center;
  }
}
</style>

