<template>
  <button class="wx-button" :class="typeClass" @click="$emit('click')" :size="size" :type="type">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'WxButton',
  props: {
    size: {
      type: String,
      default: 'mini'
    },
    type: {
      type: String,
      default: 'primary'
    }
  },
  computed: {
    typeClass () {
      return `wx-button-${this.type}`
    }
  }
}
</script>

<style lang="less">
.wx-button {
  width: 80%;
  margin: 0 auto;
  display: block;
  &.wx-button-info {
    background-color: #409EFF;
    color: #fff;
  }
  &.wx-button-danger {
    background-color: #F56C6C;
    color: #fff;
  }
}
</style>