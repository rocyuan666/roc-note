Vue3.0的beta版发布了，尤大4.17号在微博发出了Vue3.0的beta，网友直呼， 【 它来了它来了，它带着秃头走来了 】，【 学不动了，太难了 】，【 秃头警告 】等等，但都是挺期待的，本人也是迫不及待的上手看了下，奈何水平有限，暂时悟出的比较少，也欢迎各方神圣前来讨论。

### 1. 目前怎么创建vue3.0项目

```bash
vue create projectName
# 此时创建的是vue2项目,cd到项目根目录
cd projectName
# 然后执行:vue add vue-next
```

![](assets/【vue】vue3.0beta体验/1.png)

完成后在“package.json”中会发现vue已经是 3.0.0-beta.1版本,目录没什么变化但是“ main.js”中代码发生了变化，看图：

![](assets/【vue】vue3.0beta体验/2.png)

![](assets/【vue】vue3.0beta体验/3.png)

### 2. 生命周期

```css
setup: 会在组件创建执行(为组件提供属性及方法，都得写在setup中，看下面代码就明白了)
onBeforeMount: dom渲染前
onMounted: dom渲染后
onBeforeUpdate: 更新变化前
onUpdated: 更新变化后
onBeforeUnmount: 组件销毁前
onUnmounted: 组件销毁后
```

与vue2相比很容易发现区别吧，基本没变，只是没有了组件创建前（beforeCreate），创建后(created)，两者可理解为setup方法；
首次进入页面会执行 setup，onBeforeMount，onMounted

### 3. reactive – 定义数据，方法

```css
<template>
  <div>
    {{data1.message}}
  </div>
</template>

setup(){
  const data1 = reactive({
    message: "我是Vue3.0beta-message"
  })

  return { data1 }
}
```

### 4. 事件方法(也可以定义在reactive中)

```css
<template>
  <div @click="fnClick">
    {{data1.message}}
  </div>
</template>

import { reactive } from 'vue'
setup(){
  const data1 = reactive({
    message: "我是Vue3.0beta-message"
  }),
  const fnClick = _ => {
    console.log("点击了")
  }

  return { data1, fnClick }
}
```

### 5. 计算属性

```css
<template>
  <div @click="fnClick">
    {{data1.message}}
    {{fnComputed}}
  </div>
</template>

import { reactive, computed } from 'vue'
setup(){
  const data1 = reactive({
    message: "我是Vue3.0beta-message",
    number: 2
  }),
  //事件处理方法
  const fnClick = _ => {
    console.log("点击了")
  }
  //计算属性方法
  const fnComputed = computed(_ => data1.number * data1.number)
  return { data1, fnClick }
}
```

个人觉得这样的好处：
vue2中我们在“data”中定义的属性多了后，不容易一下子找到属性对应的含义，vue3这样我们可以将一个组件中的功能再次进行细分，都打包在一个对象中，也便于维护…
通过一个小项目可以看出来，附上地址：
[https://github.com/yuanpeng666/vue3.0_beta_music](https://github.com/yuanpeng666/vue3.0_beta_music)
