## xp-miniui

基于mpvue的小程序组件库

<p align="center"><img width="100" src="https://ws4.sinaimg.cn/large/006tNc79gy1fqel9fd0qyj30e80e8gmb.jpg" alt="xp-miniui logo"></p>

### 使用

> npm i xp-miniui --save

目前mpvue支持的单文件vue组件，所以使用的时候应该引入具体的组件，例如

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
