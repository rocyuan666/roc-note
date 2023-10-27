## 基本使用：

```vue
<h2>{{num}}</h2>
<!-- 不需要传参的时候可以省略 方法的括号() -->
<button v-on:click="add" type="button">+</button>
<!-- 简写 -->
<button @click="sub" type="button">-</button>

data: {
	num: 0
},
methods: {
	add(){
		this.num++;
	},
	sub(){
		this.num--;
	}
}
```

## v-on的参数问题：

```vue
<!-- 1.事件调用的方法没有参数 -->
<button @click="btn1Click()">按钮1</button>
<button @click="btn1Click">按钮1</button>
			
<!-- 2.事件调用的方法需要传入参数，1.不传参数：形参会是undedifed  2.不带()：Vue默认会将浏览器生成的 event对象 传入形参 -->
<button @click="btn2Click(123)">按钮2</button>
<button @click="btn2Click()">按钮2</button>
<button @click="btn2Click">按钮2</button>
			
<!-- 3.事件调用的方法需要传参，又要获取event对象 -->
<!-- 手动获取 浏览器的 event对象    加$event -->
<button @click="btn3Click(123,$event)">按钮3</button>
```

## v-on的修饰符:

```vue
<!-- 1. .stop 修饰符的使用 阻止事件冒泡 -->
<div @click="divClick">
	bbbbb
	<button @click.stop="btnClick">按钮1</button>
</div>
			
<!-- 2. .prevent 修饰符的使用 阻止默认事件 -->
<form action="baidu">
	<input type="submit" value="提交" @click.prevent="submitClick">
</form>
			
<!-- 3. .enter 监听某个键盘的键帽 -->
<input type="text" @keyup.enter="keyUp">
			
<!-- 4. .once 只会触发一次 -->
<button @click.once="btn2Click">按钮2</button>

<!-- 5.监听组件的原生事件时要加 .native -->
<mybtn @click.native="mybtnClick"></mybtn>
```
