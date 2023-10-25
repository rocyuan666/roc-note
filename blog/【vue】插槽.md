## 默认插槽：
```vue
<child-component>rocyuan</child-component>

Vue.component('child-component',{
    template:`
        <div>
            Hello,World!
            <slot></slot>
        </div>
    `
})

// 将 child-component 中的内容会插入到 slot 中
```
## 具名插槽：
```vue
<child-component>
    <h1 slot="center">中间的</h1>
    <h1 slot="left">中间的</h1>
    <h1>默认的</h1>
</child-component>

Vue.component('child-component',{
    template:`
        <div>
            Hello,World!
            <slot name="center"></slot>
            <slot name="left"></slot>
            <slot></slot>
        </div>
    `
})
```
## 作用域插槽：
也可理解为带数据的插槽；如果我们v-for循环渲染表格，表格每行都有本行的数据，有一列是需要进行功能操作数据的，这样我们就可以使用作用域插槽拿到本行的数据进行操作
```vue
已被废弃:
<slot-example>
  <template slot-scope="slotProps">
    {{ slotProps}}
  </template>
</slot-example>

使用这种：
<template>
  <template v-slot="{ msg }">
    {{ msg }}
  </template>
</template>
或：
<view v-for="item in dataList" key="item.id">
  <template v-slot:default="item">
    <!-- 此处添加插槽内容 -->
    <view class="cont-item">
      <view class="title">{{item.title}}</view>
    </view>
  </template>
</view>
```
