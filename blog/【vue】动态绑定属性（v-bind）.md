## 基本使用：
```vue
<img v-bind:src="imgUrl" alt="">
<a v-bind:href="aUrl">{{aName}}</a>

<!-- 简写 -->
<img :src="imgUrl" alt="">
<a :href="aUrl">{{aName}}</a>

data: {
  imgUrl:"https://img14.360buyimg.com/babel/s190x240_jfs/t1/73611/34/16563/10157/5ddf5f8bE1609147d/4ec959f1cfa2de36.png!cc_190x240.webp",
  aName: "百度一下",
  aUrl: "http://www.baidu.com"
}
```
## v-bind动态绑定class(对象语法)：
```vue
.act{color:#f00;}

<!-- 不会覆盖  原来的class -->
<div class="title" :class="{'act': isActive}">{{message}}</div>

data: {
  message: "你好啊",
  isActive: true
},
```
## v-bind动态绑定class(数组语法)：
```vue
.aaa{}
.bbb{}

<!-- 数组语法不常用 不会覆盖原来的class -->
<h2 class="title" :class="[active, line]">{{message}}</h2>

data: {
  message: "你好啊",
  active: 'aaa',
  line: 'bbb'
}
```
## v-bind动态绑定style(对象语法)：
```vue
<h2 :style="{fontSize: this.size + 'px', backgroundColor: this.bgc}">{{message}}</h2>

data: {
  message: "你好啊",
  size: 50,
  bgc: '#f00'
},
```
## v-bind动态绑定style(数组语法)：
```vue
<h2 :style="[baseStyle]">{{message}}</h2>
data: {
  message: "你好啊",
  baseStyle: {backgroundColor: '#f00'}
},
```
