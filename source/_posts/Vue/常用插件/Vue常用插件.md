---
title: Vue常用插件
data: 2021/12/29
updated: 2021/12/29
tag: Vue npm
categories: 技术
---

# 跑马灯

使用环境：

Vue3.2 + Vite + yarn

插件名称：vue-marquee-text-component

github：https://github.com/EvodiaAut/vue-marquee-text-component

使用版本：v2.0.1

API 文档：可直接查看 [github](https://github.com/EvodiaAut/vue-marquee-text-component)

| Prop     | Type    | Default | Description                                                       |
| -------- | ------- | ------- | ----------------------------------------------------------------- |
| duration | Number  | 15      | Animation Duration                                                |
| repeat   | Number  | 2       | Number of repeat the Slot (It's important for to short content)   |
| paused   | Boolean | false   | The property specifies whether the animation is running or paused |
| reverse  | Boolean | false   | Set animation-direction to reverse                                |

单行文本使用：

```html
<script setup>
  import Marquee from 'vue-marquee-text-component'
</script>

<template>
  <marquee>我是跑马灯~~~</marquee>
</template>
```

数据列表: 通过动态数据插入需要绑定:key

```html
<script setup>
  import { ref } from 'vue'
  import Marquee from 'vue-marquee-text-component'
  const marqueeText = ref('')

  // 自行调用getMarueeText赋值marqueeText
  const getMarqueeText = () => {
    data.forEach(item => {
      marqueeText.value += item.msg
    })
  }
</script>

<template>
  <marquee :duration="180" :repeat="1" :key="marqueeText"> {{marqueeText}} </marquee>
</template>
```

---

# vConsole

使用场景：WebView 中使用 Vue 项目时，方便查看控制台信息

使用环境：

Vue3.2 + Vite + yarn

插件名称：vConsole

github：https://github.com/Tencent/vConsole

使用版本：^3.9.3

```js
// main.js

import VConsole from 'vconsole'

if (import.meta.env.VITE_ENV !== 'pro') {
  new VConsole()
}
```
