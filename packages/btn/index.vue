<template>
  <button :class="computedCls" :disabled="disabled" :hover-class="hoverClass" @click="onClick">
    {{text}}
  </button>
</template>

<script>
export default {
  name: 'btn',
  props: {
    className: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'primary'
    },
    size: {
      type: String,
      default: 'default'
    },
    disabled: {
      type: Boolean,
      default: false
    },
    hoverClass: {
      type: String,
      default: 'none'
    },
    text: {
      type: String,
      default: '按钮'
    }
  },
  computed: {
    computedCls() {
      let classes = ['mnui-btn', 'mnui-btn-' + this.type, 'mnui-btn-' + this.size]
      if (this.disabled) classes.push('mnui-btn-disabled')
      if (this.className) classes.push(this.className)
      return classes.join(' ')
    }
  },

  methods: {
    onClick(e) {
      this.$emit('click', e)
    }
  }
}
</script>

<style scoped>
.mnui-btn::after {
  border: none;
}
.mnui-btn {
  border: none;
  box-sizing: border-box;
  display: inline-block;
  text-align: center;
  width: 100%;
  height: 92px;
  line-height: 92px;
  font-size: 36px;
  border-radius: 6px;
}
.mnui-btn-small {
  width: 300px;
  height: 88px;
  line-height: 88px;
  font-size: 32px;
  border-radius: 6px;
}
.mnui-btn-tiny {
  width: 160px;
  height: 72px;
  line-height: 72px;
  font-size: 28px;
  border-radius: 4px;
}
.mnui-btn-primary {
  color: #fff;
  background-color: #1ccada;
}
.mnui-btn-plain {
  color: #1ccada;
  background-color: transparent;
  border: 2px solid #1ccada;
}
.mnui-btn-white {
  color: #fff;
  background-color: transparent;
  border: 2px solid #fff;
}
.mnui-btn-circle {
  width: 220px;
  height: 220px;
  background-color: #1ccada;
  border-radius: 50%;
}
.mnui-btn-disabled {
  color: rgba(0, 0, 0, 0.3);
  background-color: #f7f7f7;
}
.mnui-btn-disabled.mnui-btn-plain {
  color: rgba(0, 0, 0, 0.3);
  background-color: transparent;
  border: 2px solid #ccc;
}
</style>
