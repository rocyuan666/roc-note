## 基本使用（全局组件）：

```vue
// 1. 创建组件构造器对象
const cpnC = Vue.extend({
	template: `
	<div>
		<h2>我是标题</h2>
		<p>我是内容111111111</p>
		<p>我是内容222222222</p>
	</div>
	`
})

// 2. 注册组件 (全局组件) (使用的标签名, 构造器的名字)
Vue.component('my-cpn', cpnC);

<!-- 3. 使用组件 多次使用 -->
<my-cpn></my-cpn>
<my-cpn></my-cpn>
```

## 组件的全局组件和局部组件:

```vue
const app = new Vue({
	el: '#app',
	data: {
		message: '你好啊'
	},
	//2. 注册组件(局部组件) 只能在app实例中使用,app2中不可以使用
	components:{
		// 标签名: 组件构造器名
		mycpn: cpnC
	}
})
const app2 = new Vue({
	el: '#app2'
})
```

## 父组件和子组件：

```vue
// 创建第一个组件 （第二个组件的子组件）
const cpnC1 = Vue.extend({
	template: `
	<div>
		<h2>我是标题1</h2>
		<p>我是内容1</p>
	</div>
	`
})
// 创建第二个组件 （第一个组件的父组件）
const cpnC2 = Vue.extend({
	template: `
	<div>
		<h2>我是标题2</h2>
		<p>我是内容2</p>
		<cpn1></cpn1>
	</div>
	`,
	components:{
		cpn1: cpnC1
	}
})
// root组件（第二个组件的父组件）
const app = new Vue({
	el: '#app',
	data: {
		message: '你好啊'
	},
	components: {
		cpn2: cpnC2
	}
})
```

## 组件的简写组件：

```vue
// 省略了 Vue.extend({})
// 全局组件（简便语法）
Vue.component('cpn2', {
	template: `
	<div>
		<h2>我是标题2</h2>
		<p>我是内容2</p>
	</div>
	`
})

const app = new Vue({
	el: '#app',
	data: {
		message: '你好啊'
	},
	// 局部组件（简便语法）
	components: {
		cpn1: {
			template: `
			<div>
			<h2>我是标题1</h2>
			<p>我是内容1</p>
			</div>
			`
		}
	}
})
```

## 组件模板的分离写法：

```vue
<!-- 1.script标签写法 -->
创建 -> 注册 -> 使用
<script type="text/x-template" id="cpn1">
	<div>
		<h2>{{title}}</h2>
		<p>我是内容1</p>
	</div>
</script>

Vue.component('cpn1', {
	template: '#cpn1',
	data(){
		return {
			title: '我是标题111'
		}
	}
})
<cpn1></cpn1>

----------------------------------------------------------

<!-- 2.template 标签写法 -->
创建 -> 注册 -> 使用
<template id="cpn2">
	<div>
		<h2>我是标题2</h2>
		<p>我是内容2</p>
	</div>
</template>
		
Vue.component('cpn2', {
	template: '#cpn2'
})

<cpn2></cpn2>
```

## 组件中的数据存放(存放在data方法的返回值，对象中)：

```vue
<template id="cpn1">
	<div>
		<h2>{{title}}</h2>
		<p>{{cont}}</p>
	</div>
</template>

Vue.component('cpn1', {
	template: '#cpn1',
	data(){
		return {
			title: '我是标题111',
			cont: '我是内容111'
		}
	}
})

<cpn1></cpn1>
```

为什么组件中的data是一个方法？
多次使用的组件不会共用一个data，因为data是一个方法，多次使用组件会多次调用data方法，每一次调用组件所用的数据是每一次调用data方法返回的对象数据。
