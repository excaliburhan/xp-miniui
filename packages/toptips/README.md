# Toptips 顶部提示

## 说明

基于mpvue开发的单文件vue组件

## 使用

### 安装组件

> npm install @miniui/toptips --save

### 引入组件

```js
<template>
  <toptips></toptips>
</template>

<script>
import toptips from '@miniui/toptips'

export default {
  components = {
    toptips
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
