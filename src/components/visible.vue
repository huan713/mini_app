<template>
  <span class="wx-visible" @click="switchClick">
    <i class="fa wx-visible-icon" :class="show ? 'fa-eye' : 'fa-eye-slash'"></i>
    <span>{{show ? '公开' : '仅自己可见'}}</span>
  </span>
</template>

<script>
export default {
  name: 'visible',
  props: {
    show: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    switchClick () {
      this.show = !this.show
      this.$emit('update:show', this.show)
    }
  }
}
</script>


<style lang="less">
.wx-visible {
  color: #999;
  font-size: 32rpx;
}
.wx-visible-icon {
  padding: 0 12rpx;
}
</style>

