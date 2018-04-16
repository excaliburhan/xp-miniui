# List 列表

## 说明

基于mpvue开发的单文件vue组件

## 使用

### 安装组件

> npm install @miniui/list --save

### 引入组件

```js
// index.vue
<template>
  <list></list>
</template>

<script>
import listGroup from '@miniui/list'

export default {
  components = {
    listGroup
  }
}
</script>
```

## props参数

### className[String]

classname

### data[Array]

列表数据

```js
{
  icon: '/static/img/icon.png', // icon地址
  title: '按钮', // 标题内容
  desc: '测试内容', // 描述内容,
  link: '/pages/user/index', // 跳转地址
  arrow: false, //是否有箭头
}
```

## event事件

### click

点击事件，会返回点击item的内容
