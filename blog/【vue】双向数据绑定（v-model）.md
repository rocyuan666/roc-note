## 基本使用：
```vue
<!-- input中改变message值，都同步改变，反之一样 -->
<input type="text" v-model="message">
<input type="text" v-model="message">
<p>{{message}}</p>

data: {
	message: '你好啊'
}
```
## v-model原理：
```vue
<!-- input值发生变化时触发clickChange方法 -->
<input type="text" :value="message" @input="clickChange($event)">
<p>{{message}}</p>

data: {
	message: '你好啊'
},
methods: {
	clickChange(event){
		this.message = event.target.value
	}
}
```
## v-model结合radio类型:
```vue
<!-- v-model相同不用 name 属性 -->
<label for="male">
	<input type="radio" id="male" value="男" v-model="sex">
	男
</label>
<label for="famale">
	<input type="radio" id="famale" value="女" v-model="sex">
	女
</label>
<p>您选择的性别是: {{sex}}</p>

data: {
	message: '你好啊',
	sex: '男'
}
```
## v-model结合checkbox类型：
```vue
<!-- 单个复选框，绑定到布尔值： -->
<label for="agree">
	<input type="checkbox" id="agree" v-model="isAgree">
	同意协议
</label>
<p>您选择的是: {{isAgree}}</p>
<button :disabled="!isAgree">下一步</button>

<!-- 多个复选框，绑定到同一个数组： -->
<input type="checkbox" value="篮球" v-model="hobbies">篮球
<input type="checkbox" value="足球" v-model="hobbies">足球
<input type="checkbox" value="乒乓球" v-model="hobbies">乒乓球
<input type="checkbox" value="羽毛球" v-model="hobbies">羽毛球
<p>您的爱好是: {{hobbies}}</p>

data: {
	message: '你好啊',
	isAgree: false,
	hobbies: []
}
```
## v-model结合select类型：
```vue
<!-- 选择一个 -->
<select name="abc" v-model="fruit">
	<option value="苹果">苹果</option>
	<option value="香蕉">香蕉</option>
	<option value="葡萄">葡萄</option>
	<option value="榴莲">榴莲</option>
</select>
<p>您选择的水果是: {{fruit}}</p>

<!-- 多选 multiple 时 (绑定到一个数组) -->
<select name="abc" v-model="fruits" multiple="multiple">
	<option value="苹果">苹果</option>
	<option value="香蕉">香蕉</option>
	<option value="葡萄">葡萄</option>
	<option value="榴莲">榴莲</option>
</select>
<p>您选择的水果是: {{fruits}}</p>

data: {
	message: '你好啊',
	fruit: '香蕉',
	fruits: ['香蕉']
}
```
## v-model修饰符的使用：
```vue
<!-- 1. .lazy: 失去焦点的时候更新 message -->
<input type="text" v-model.lazy="message">
<p>{{message}}</p>
			
<!-- 2. .number: v-model绑定的都是string类型, .number 可转换为number类型 -->
<input type="number" v-model.number="age">
<p>{{age}}-{{typeof age}}</p>
			
<!-- 3. .trim 去掉两端空格 -->
<input type="text" v-model.trim="name">
<p>{{name}}</p>
```
