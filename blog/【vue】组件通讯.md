## 组件父传子：

子组件中使用 props 接收父组件传过来的值。

```vue
// 父传子:
<div id="app">
	<cpn :cmessage='message' :cmovies='movies'></cpn>
</div>

const cpn = {
	template: '#cpn',
	// 1.数组写法
	// props: ['cmessage', 'cmovies'],
	// 2.对象写法（常用）
	props: {
		// 2.1 类型的限制
		// cmessage: String,
		// cmovies: Array
		// 2.2 提供默认值  及必传值
		cmessage: {
			type: String,
			default: 'aaaa',
			required: true
		},
		cmovies: {
			type: Array,
			// default: []    vue2.5.x 以下可以
			default(){
				return []
			}
		}
	},
	data(){
		return {}
	}
}

const app = new Vue({
	el: '#app',
	data: {
		message: '你好啊',
		movies: ['海王', '海贼王', '海尔兄弟']
	},
	components:{
		cpn: cpn
	}
})
```

## 组件子传父：

子组件使用 $emit 发送 自定义事件并可携带参数，父组件使用绑定自定义事件触发自身定义的方法，在自身定义的方法中接收到携带的参数。

```vue
<cpn @itemclick='btnClick'></cpn>

<template id="cpn">
	<div>
		<button v-for="item in cts" @click="btnClick(item)">{{item.name}}</button>
	</div>
</template>

//子组件
const cpn = {
	template: '#cpn',
	data(){
		return {
			cts:[
				{id: 'aaa', name: '热门推荐'},
				{id: 'bbb', name: '手机数码'},
				{id: 'ccc', name: '家用家电'},
				{id: 'ddd', name: '电脑办公'}
			]
		}
	},
	methods: {
		btnClick(item){
			// console.log(item);
			// 向父组件 发射事件: 自定义事件
			this.$emit('itemclick',item)
		}
	}
}
//父组件
const app = new Vue({
	el: '#app',
	data: {
		info: {
			name: 'roc',
			age: 18,
			height: 180
		}
	},
	components:{
		cpn
	},
	methods:{
		btnClick(item){
			console.log('btnClick',item)
		}
	}
})
```

## 父组件访问子组件：

通过给子组件添加属性 ref ，父组件可以用 $refs 拿到子组件对象。

```vue
<div id="app">
	<cpn ref='bbb'></cpn>
	<cpn ref='aaa'></cpn>
	<cpn></cpn>
	<button @click="btnclick">按钮</button>
</div>

methods: {
	btnclick(){
		// 用的比较少依  赖于下标 $children (数组类型)
		// console.log(this.$children);
		// this.$children[0].showMessage()
		// console.log(this.$children[0].name)
	
		// 用的多 $refs  (对象类型)
		console.log(this.$refs.aaa.name);
	}
},
```

## 子组件访问父组件（使用较少）：

子组件使用 $parent 可访问到父组件对象，使用 $root 可访问到根组件

```vue
methods: {						
	btnClick(){
		//  $parent  为了组件的复用性 子访问父 用的少
		console.log(this.$parent.name)
		//  $root  访问根组件 用的少
		console.log(this.$root.message)
	}
}
```
