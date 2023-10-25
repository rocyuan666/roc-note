## v-if使用：
```vue
<h2 v-if="isShow">
	<p>{{message}}</p>
</h2>

data: {
	message: 'hello',
	isShow: false
}
```
## v-if和v-else的使用：
```vue
<h2 v-if="isShow">
	<p>{{message}}</p>
</h2>
<h1 v-else>isShow为false时，显示我</h1>

data: {
	message: 'hello',
	isShow: true
}
```
## v-if和v-else-if和v-else的使用：
```vue
<h2 v-if="score >= 90">优秀</h2>
<h2 v-else-if="score >= 80">良好</h2>
<h2 v-else-if="score >= 60">及格</h2>
<h2 v-else>不及格</h2>

data: {
	score: 90
}
```
## v-show的使用（v-if，v-show区别）：
```vue
<!-- 
v-if: 条件为 false 时；包含v-if的Dom不会存在在页面中（适用于切换频率低）
v-show: 条件为 false 时；包含v-show的Dom存在页面中，只是加了 display:none 行内样式（适用于切换频率高）
-->
<h2 v-if="isShow" id="aaa">{{message}}</h2>

data: {
	message: '你好啊',
	isShow: true
}
```
