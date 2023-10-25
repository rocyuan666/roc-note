## 基本使用：
```vue
<h2>{{firstName + " " + lastName}}</h2>
<!-- 计算属性 -->
<h2>{{fullName}}</h2>

// 计算属性 computed
computed: {
	fullName: function(){
		return this.lastName + ' ' + this.firstName
	}
}
```
## 进阶使用：
```vue
<h2>总价格：{{prices}}</h2>

data: {
	books: [
		{id: 110, name: 'xxxxxx', price: 110},
		{id: 111, name: 'xxxxxx', price: 111},
		{id: 112, name: 'xxxxxx', price: 112},
		{id: 113, name: 'xxxxxx', price: 113},
	]
},
computed: {
	// 计算books中书的总价格
	prices: function(){
		// 总价格
		let prices = 0;						
		for(let i in this.books){
			prices += this.books[i].price;
		}
		return prices;
	}
}
```
## 计算属性的setter和getter：
```vue
<h2>{{fullName}}</h2>

data: {
	fristName: 'aaa',
	lastName: 'bbb'
},
computed: {
	fullName: {
		// 一般没有set方法，只读属性
		// 如果有，对fullName赋值会触发set方法，对fullName赋的值是newvalue
		set: function(newvalue){
			console.log(newvalue)
		},
		get: function(){
			return this.fristName + ' ' + this.lastName;
		}
	}
}
```
## computed和methods区别
多次执行时， computed 只执行1次methods会执行多次。
