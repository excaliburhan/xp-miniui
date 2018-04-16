## xp-miniui

基于mpvue的小程序组件库

![xp-mnui](https://ws1.sinaimg.cn/large/006tKfTcgy1fm2gtok88bg30j40agjx7.gif)

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
