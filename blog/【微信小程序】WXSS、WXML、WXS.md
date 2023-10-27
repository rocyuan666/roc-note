### WXSS

1. 行内（内联）样式：style  
2. 页面（外联）样式 class id …  
3. 全局样式 app.wxss  

权重 ： 行内 > 页面 > 全局

**单位：**

wxss单位：rpx (小程序适配)  
iphone6（750）为标准：1px == 2rpx

**样式导入：**

可以在app.wxss中导入这个样式 ；也可以在page.wxss导入这个样式
@import “路径”

**官方样式库：**

WeUI.wxss基本样式库 ： [https://github.com/Tencent/weui-wxss](https://github.com/Tencent/weui-wxss)

### WXML

wxml只能用wx中的组件 view, text, image… ； 大小写敏感 class Class不同

**1）Mustache语法** ：{{message}}

**2）逻辑判断 wx:if …**

```vue
wx:if
wx:elif
wx:else

hidden

wx:if 与 hidden区别（v-if v-show）： v-if="false"在dom中没有不存在，hidden只是添加了display： none
```

**3）列表渲染 wx:for**

```vue
1. 遍历数组、字符串、数字
  item index，会自动生成的
  <view wx:for="{{[1, 2, 3, 4]}}">{{item}} {{index}}</view>
  <view wx:for="rocyuan">{{item}} {{index}}</view>
  <view wx:for="{{5}}">{{item}}</view>  // 01234

2. block标签：包裹一组组件的标签 并非组件（不会在界面上渲染，只接收控制属性）
  <block></block>

3. item/index起名字
  wx:for-item="inner_item"
  wx:for-index="inner_index"

  <view wx:for="{{arr}}" 
        wx:for-item="inner_item"
        wx:for-index="inner_index">
        {{inner_item}} {{inner_index}}
  </view>

4. wx:key（唯一标识）
  没有key：中间改变一项，后面全都会变
  有key：利用key直接复用更改后的虚拟dom
  <view wx:for="{{arr}}" wx:key="{{index}}">{{item}}</view>

key的作用主要是为了高效的更新虚拟DOM。
```

**4）模板用法 template**

WXML提供**模板（template），**可以在模板中定义代码片段，在不同的地方调用。(是一种wxml代码的复用机制) ;
使用 name 属性，作为模板的名字, 然后在 <template/> 内定义代码片段

```vue
<!-- 
  基本使用
  template包裹的内容,没有被使用，是不会被渲染的
  使用 is="name"
 -->
<template name="content">
  <button>按钮</button>
  <view>哈哈</view>
</template>
<template is="content"></template>
<template is="content"></template>
<!-- 带数据 -->
<template name="content">
  <button>{{btnText}}</button>
  <view>{{content}}</view>
</template>
<template is="content" data="{{btnText: "按钮", content: "哈哈哈"}}"></template>
<template is="content" data="{{btnText: "按钮", content: "哈哈哈"}}"></template>
```

**5）wxml的引入**

```vue
<!-- 
  1）import: 
    主要导入template
    不可以多个连接导入
  2）include:
    将wxml中的公共组件抽取到一个文件中导入
    不能导入template、wxs，可以多个连接导入
 -->
 <import src="template.wxml"/>
 <include src="page.wxml"/>
```

### WXS

[https://developers.weixin.qq.com/miniprogram/dev/reference/wxs/](https://developers.weixin.qq.com/miniprogram/dev/reference/wxs/)

WXS（WeiXin Script）是小程序的一套脚本语言，结合 WXML，可以构建出页面的结构。
WXS 与 JavaScript 是不同的语言，有自己的语法，并不和 JavaScript 一致。
以上摘自官方文档，但个人觉得 基本一致

**为什么要用wxs？**

在WXML中是不能直接调用Page、Component中定义的方法的；
但某些情况, 我们希望使用方法来处理WXML中的数据(类似于Vue中的过滤器)，这个时候就使用WXS了。

**wxs写法**

1） 写在<wxs>标签中

```vue
  <wxs module="info">
  //js代码
  var message = "消息"
  var name = "rocyuan"
  //wxml中就可以使用此方法
  var add = function(a, b){
    return a+b
  }

  module.exports = {
    message: message,
    name: name,
    add: add
  }
</wxs>
<view>{{info.message}}</view>
<view>{{info.name}}</view>
<view>{{info.add(1,2)}}</view>
```

2）写在以.wxs结尾的文件中

```vue
<!-- 不能使用绝对路径的，必须相对路径 -->
<wxs src="../../wxs/info.wxs" module="info" />
<view>{{info.message}}</view>
<view>{{info.name}}</view>
<view>{{info.add(1,2)}}</view>
```
