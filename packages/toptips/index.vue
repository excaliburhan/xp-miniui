<template>
  <div class="mnui-toptips animated" :class="computedCls" v-show="display">
    <div class="mnui-toptips-mask"></div>
    <div class="mnui-toptips-wrap" :class="className">
      <div class="mnui-toptips-text">{{title}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'toptips',
  props: {
    className: {
      type: String,
      default: ''
    },
    title: {
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
.animated {
  transition: opacity 0.4s;
}
.mnui-toptips {
  opacity: 0;
  position: fixed;
  z-index: 9999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.mnui-toptips.is-show {
  opacity: 1;
}
.mnui-toptips-mask {
  position: fixed;
  z-index: 1000;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.mnui-toptips-wrap {
  box-sizing: border-box;
  position: fixed;
  z-index: 5000;
  top: 0;
  left: 0;
  right: 0;
  min-height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 15px 20px;
  font-size: 30px;
  color: #fff;
  background-color: rgba(0, 0, 0, 0.7);
}
.mnui-toptips-text {
  text-align: center;
}
</style>
