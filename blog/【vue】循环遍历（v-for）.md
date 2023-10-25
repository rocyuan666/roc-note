## v-for遍历数组：
```vue
<ul>
	<li v-for="(item, index) in names">{{index+1}}. {{item}}</li>
</ul>

data: {
	names: ['roc','koke','sev']
}
```
## v-for遍历对象：
```vue
<ul>
	<li v-for="(value, key, index) in info">{{index}} - {{key}} : {{value}}</li>
</ul>

data: {
	info: {
		name: 'roc',
		age: 18,
		height: 180
	}
}
```
## v-for使用过程需添加key：
```vue
// 官网：建议尽可能在使用 v-for 时提供 key attribute，除非遍历输出的 DOM 内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。
// vue会复用渲染的组件（dom）从而不会重新渲染，加key保证唯一性，不会复用将重新渲染。
<ul>
	<li v-for="item in letters" :key="item">{{item}}</li>
</ul>

data: {
	letters: ['a', 'b', 'c', 'd', 'e']
}
```
## 数组响应式的方法：
```vue
// 通过索引修改数组中的元素，不会发生响应式
this.letters[0] = 'aaa';
// -----------------------------------------------------------------------
// 响应式的方法：
// 1.push方法(向最后添加元素，可添加多个)
this.letters.push('aaa');
						
// 2.pop方法(删除最后一个)
this.letters.pop();
						
// 3.unshift方法(向最前面添加，可添加多个)
this.letters.unshift('aaa')
						
4.shift方法(删除第一个)
this.letters.shift();
						
// splice作用：删除元素/插入元素/替换元素  (常用  推荐使用)
// 5.splice方法(a,b,...c)  a:开始的位置(包含开始位置)  b:要删除多少个(没传 删除后面所有)  ...c添加的元素
this.letters.splice(1, 0, 'aaa','bbb')
						
// 6.sort方法(排序)
this.letters.sort();
						
// 7.reverst方法(反转)
this.letters.reverse();
						
// set('要修改的对象','索引值','修改后的值')
Vue.set(this.letters, 0, 'aaa')
```
