# Toast 轻提示

## 说明

基于mpvue开发的单文件vue组件

## 使用

### 安装组件

> npm install @miniui/toast --save

### 引入组件

```js
<template>
  <toast></toast>
</template>

<script>
import toast from '@miniui/toast'

export default {
  components = {
    toast
  }
}
</script>
```

## props参数

### className[String]

classname

### title[String]

显示的文字

### duration[Number]

持续时间，默认1500ms

### visible

是否可见
