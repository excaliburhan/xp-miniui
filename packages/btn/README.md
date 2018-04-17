# Btn 按钮

## 说明

基于mpvue开发的单文件vue组件

## 使用

### 安装组件

> npm install @miniui/btn --save

### 引入组件

```js
<template>
  <btn></btn>
</template>

<script>
import btn from '@miniui/btn'

export default {
  components = {
    btn
  }
}
</script>
```

## props参数

### className[String]

classname

### type[String]

按钮样式，默认为primary，可选plain、white

### size[String]

按钮大小，可选small，tiny

### disabled[Boolean]

是否disabled

### hoverClass[String]

点击态样式classname，默认为none

### text[String]

按钮样式

## event事件

### click

点击事件
