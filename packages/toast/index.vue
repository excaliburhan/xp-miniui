<template>
  <div class="mnui-toast animated" :class="computedCls" v-show="display">
    <div class="mnui-toast-mask">
      <div class="mnui-toast-wrap" :class="computedWrapCls">
        <div class="mnui-toast-icon" :class="computedIconCls" v-if="icon">
          <img :src="computedIconUrl" alt="">
        </div>
        <div class="mnui-toast-image" :class="computedIconCls" v-if="!icon && image">
          <img :src="image" alt="">
        </div>
        <div class="mnui-toast-text">{{title}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'toast',
  props: {
    className: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    icon: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    duration: {
      type: Number,
      default: 1500
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      show: false,
      display: false,
      transitionTimer: null,
      syncTimer: null
    }
  },
  computed: {
    computedCls() {
      const classes = []
      if (this.show) classes.push('is-show')
      return classes.join(' ')
    },
    computedWrapCls() {
      const classes = []
      if (this.className) classes.push(this.className)
      if (this.icon || this.image) classes.push('is-icon')
      return classes.join(' ')
    },
    computedIconCls() {
      if (this.icon) {
        return 'is-' + this.icon
      }
      if (this.image) {
        return 'is-image'
      }
      return ''
    },
    computedIconUrl() {
      let suffix = 'png'
      if (this.icon === 'loading') suffix = 'svg'
      if (this.icon) {
        return `https://static.excaliburhan.com/mnui/mnui-${this.icon}.${suffix}`
      }
      return ''
    }
  },
  watch: {
    visible(v) {
      this.show = v
    },
    show(v) {
      // transition
      if (this.transitionTimer) {
        clearTimeout(this.transitionTimer)
      }
      if (v) {
        this.display = v
      }
      this.transitionTimer = setTimeout(() => {
        this.display = v
      }, 400)
      // sync
      if (this.syncTimer) {
        clearTimeout(this.syncTimer)
      }
      // duration为0表示不主动消失
      if (this.duration !== 0) {
        if (v) {
          this.syncTimer = setTimeout(() => {
            this.show = false
            this.$emit('update:visible', false)
          }, this.duration)
        }
      }
    }
  },

  created() {
    this.show = this.visible
  }
}
</script>

<style scoped>
@keyframes mnuiLoading {
  0% {
    transform: rotate3d(0, 0, 1, 0deg);
  }
  100% {
    transform: rotate3d(0, 0, 1, 360deg);
  }
}
.animated {
  transition: opacity 0.4s;
}
.mnui-toast {
  opacity: 0;
  position: fixed;
  z-index: 9999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.mnui-toast.is-show {
  z-index: 9999;
  opacity: 1;
}
.mnui-toast-mask {
  position: fixed;
  z-index: 1000;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.mnui-toast-wrap {
  box-sizing: border-box;
  position: fixed;
  z-index: 5000;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-width: 40%;
  max-width: 60%;
  min-height: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 15px 20px;
  font-size: 30px;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.7);
  border-radius: 10px;
}
.mnui-toast-wrap.is-icon {
  min-width: 240px;
  min-height: 240px;
  width: 240px;
}
.mnui-toast-text {
  text-align: center;
}
.mnui-toast-icon,
.mnui-toast-image {
  margin-bottom: 32px;
}
.mnui-toast-icon img {
  width: 100%;
  height: 100%;
}
.mnui-toast-image img {
  width: 80px;
  height: 80px;
}
.mnui-toast-icon.is-success {
  width: 99px;
  height: 71px;
}
.mnui-toast-icon.is-loading {
  width: 76px;
  height: 76px;
  animation: mnuiLoading 1s steps(12, end) infinite;
}
.mnui-toast-icon.is-warn {
  width: 14px;
  height: 86px;
}
</style>
