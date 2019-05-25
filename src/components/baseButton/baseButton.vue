<template>
  <button class="button-inner" :class="[type, round]" v-bind="$attrs">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      round: ''
    }
  },
  created () {
    if (Object.keys(this.$attrs).includes('round')) {
      this.round = 'round'
    }
  }
}
</script>

<style scoped>
.button-inner {
  appearance: none;
  width: 104px;
  height: 40px;
  border: 1px solid #dcdfe6;
  outline: none;
  background: #fff;
  border-radius: 4px;
  font-size: 14px;
}
.primary {
  background: #409eff;
  border-color: #409eff;
  color: #fff;
}
.success {
  background: #67c23a;
  border-color: #67c23a;
  color: #fff;
}
.info {
  background: #909399;
  border-color: #909399;
  color: #fff;
}
.warning {
  background: #e6a23c;
  border-color: #e6a23c;
  color: #fff;
}
.danger {
  background: #f56c6c;
  background-color: #f56c6c;
  color: #fff;
}
.round {
  border-radius: 20px;
}
</style>
