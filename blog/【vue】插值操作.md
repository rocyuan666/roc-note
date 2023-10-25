## Mustache语法
 {{ }}
```vue
<h2>{{message}}</h2>
```
## v-once
只会在初始化的时候赋值，不会根据数据变化而变化
```vue
<h2 v-once>{{message}}</h2>
```
## v-html
展示html代码段
```vue
<h2 v-html="url"></h2>

let vm = new Vue({
	el: "#app",
	data: {
		message: "你好啊",
		url: '<a href="http://www.baidu.com">百度一下</a>'
	}
});
```
## v-text
一般不用 缺点：不灵活 会覆盖标签内内容
```vue
<h2 v-text="message"></h2>
```
## v-pre
把内容原封不动的解析出来
```vue
<h2 v-pre>{{message}}</h2>
```
## v-cloak
（斗篷）解析之前会有v-cloak，解析完成后会去掉
```vue
[v-cloak] {
	display: none;
}
<h2 v-cloak>{{message}}</h2>
```
