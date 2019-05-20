<template>
  <div class="select-wrapper" v-click-outside>
    <input type="text"
      :value="label"
      readonly
      class="input"
    >
    <transition name="el-zoom-in-top">
      <ul class="select" v-show="isVisiable">
        <slot></slot>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  directives: {
    clickOutside: {
      bind (el, bindings, vnode) {
        let handler = e => {
          if (el.contains(e.target)) {
            if (!vnode.context.isVisiable) {
              vnode.context.focus()
            } else {
              vnode.context.blur()
            }
          } else {
            if (vnode.context.isVisiable) {
              vnode.context.blur()
            }
          }
        }
        el.handler = handler
        document.addEventListener('click', handler)
      },
      unbind (el) {
        document.removeEventListener('click', el.handler)
      }
    }
  },

  props: {
    value: {
      type: String,
      default: ''
    }
  },

  data () {
    return {
      isVisiable: false,
      label: ''
    }
  },

  mounted () {
    this.$nextTick(() => {
      this.$children.forEach(item => {
        if (item.value === this.value) {
          this.label = item.label
        }
      })
    })
  },

  watch: {
    isVisiable (value) {
      if (value) {
        setTimeout(() => {
          this.$children.forEach(item => {
            if (item.label === this.label) {
              item.isActive = true
              item.isHover = true
            } else {
              item.isActive = false
              item.isHover = false
            }
          })
        }, 20);
      }
    }
  },

  methods: {
    handleSelect (value, label, _uid) {
      this.label = label
      this.$emit('input', value)
      this.$children.forEach(item => item.isActive = item._uid === _uid)
    },

    handleHover (_uid) {
      this.$children.forEach(item => item.isHover = item._uid === _uid)
    },

    focus () {
      this.isVisiable = true
    },

    blur () {
      this.isVisiable = false
    },

    handleClick () {
      this.isVisiable = !this.isVisiable
    }
  }
}
</script>

<style scoped>
.input {
  outline: none;
  height: 40px;
  border-radius: 4px;
  border: 1px solid #e4e7ed;
  padding: 0 15px;
}
.select {
  position: absolute;
  z-index: 88;
  left: 0;
  top: 120%;
  display: inline-block;
  border: 1px solid #e4e7ed;
  border-radius: 4px;
  width: 100%;
  overflow: hidden;
  padding: 6px 0;
  background: #fff;
}
.select-wrapper {
  display: inline-block;
  position: relative;
}

.el-zoom-in-top-enter-active,
.el-zoom-in-top-leave-active {
  opacity: 1;
  transform: scaleY(1);
  transition: transform 300ms cubic-bezier(0.23, 1, 0.32, 1), opacity 300ms cubic-bezier(0.23, 1, 0.32, 1);
  transform-origin: center top;
}
.el-zoom-in-top-enter,
.el-zoom-in-top-leave-active {
  opacity: 0;
  transform: scaleY(0);
}
</style>

