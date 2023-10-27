## 类型基本用法：

### 字符串 string

```typescript
let a: string = 100;
```

### 数字 number

```typescript
let a: number = 100;
```

### 数组 xxxtype\[\]

```typescript
let a: string[] = ["roc1", "roc2"];
```

### null

```typescript
let a: null = null;
```

### undefined

```typescript
let a: undefined = undefined;
```

### 任意 any

```typescript
// 任意类型，不做类型判断，等同于使用js原生，可以随意使用
let a: any = "roc";
let b: any = 123;
let c: string = b; // success any类型可以随意使用
console.log(c)
```

### 未知 unknown

```typescript
// 不知道类型，与any不同，不可随意使用
let a: unknown = "roc";
let b: unknown = 123;
let c: string = b; // error unknown类型不能赋值给string类型
console.log(c)
```

### 空 void

```typescript
// 空值，也可返回 null undefined
function fn(): void {
	// return null
  // return undefined
  // 也可不写
}
```

### 从未 never

```typescript
// 从未（永不可能的意思）
function fn(): never {
	while(true){}
}
function fn(arg: string | number) {
	switch (typeof arg) {
		case "string":
			console.log("string类型处理");
			break;
		case "number":
			console.log("number类型处理");
			break;
		default:
			const check: never = arg;
	}
}
fn("roc")
fn(true) // error, 比如封装fn方法，指定类型做处理，其他类型报错（利用never类型永远不可能被其他类型赋值，警告调用者）
```

### 元组 tuple \[xxxtype\]

```typescript
// 多种元素的组合（指定位数及类型的数组），比如react hook中的useState的返回值
let a: [string, number, number] = ["roc", 18, 200]
```

### 函数参数&返回值类型

```typescript
// 1.普通函数
function add(a: number, b: number): number {
	return a + b;
}
// 2.匿名函数
// 如下：匿名函数的"item"不需要指定类型（当然写上": string"也可以），因为arr里每一项的类型都是确定的，ts内部会自动推导出"item"类型
const arr: string[] = ["roc1", "roc2", "roc3"];
arr.forEach((item) => {
	console.log(item);
})
```

### 对象类型 {}

```typescript
const obj: {a: number, b: string} = {a: 123, b: "roc"}
```

### 可选类型 ?

```typescript
// 用 "?" 可选类型，可传可不传；不传的话则是undefined
// 实际上c属性就是：number与undefined的联合类型
const obj: {a: number, b: string, c?: number} = {a: 123, b: "roc", c: 200}
```

### 联合类型 |

```typescript
用 "|" 可以有多个类型；但是内部一般需要进行类型判断处理
function fn(id: string | number | boolean) {
	console.log(id);
}
```

### 类型别名 type

```typescript
用"type"关键字定义类型
type myType = string | number | boolean;
let my: myType = "roc";

type objType = {
	a: string,
  b: number
}
let obj: objType = {
	a: "roc",
  b: 18
}
```

### 类型断言 as

```typescript
// 我们明确知道改数据的类型时，可以用 as 指定

// 此时el的类型是 HTMLElement，并没有 src属性
const el document.getElementById("roc")
el.src = ""; // error

// 但是我们如果是一个img元素，id为“roc”,那它就应该有src属性
const el document.getElementById("roc") as HTMLImageElement
el.src = ""; // success

不推荐使用
let a = "roc";
let b: number = a as any as number;
let c: number = a as unknown as number;
```

### 非空类型断言 !

```typescript
// 表示可以确定某个标识符是有值的，跳过ts在编译阶段的检查

// 下面代码编译时会报错，因为msg是可选的 也可能是undefined类型
function printMsg(msg?: string) {
	console.log(msg.length);
}

// 使用非空断言，编译通过
function printMsg(msg?: string) {
	console.log(msg!.length)
}
```

### 可选链 ?.

它不是ts的语法特性，是ES11（ES2020）的语法特性

```typescript
// 作用是当属性不存在的时候会短路，会返回undefined
type infoType = {
	name: string,
	age?: number,
	friend?: {
		name: string,
		age?: number
	}
}

const info: infoType = {
	name: "roc",
	friend: {
		name: "abc"
	}
}

console.log(info.name)
// console.log(info.friend.name) // error 因为info.friend很有可能是不存在的，当然也可以使用ts的非空断言!，但是它会跳过检查，不推荐
console.log(info.friend?.name) // success
```

### !!

本就是javascript语法

```typescript
// !! 把其他类型转换为boolean 实际上就是 两次取反
let a = "hello";
let b = !!a // 相当于 先!a隐式类型转换为false，再次进行取反!false -> true

```

### ??

空值合并操作符是一个逻辑操作符；当左侧是null或者undefined时，返回右侧的操作数，否则返回左侧的操作数；与逻辑或 || 类似

```typescript
let a: string | null = "roc";
let b = a ?? "rocyuan";
console.log(b) // roc

let a: string | null = null;
let b = a ?? "rocyuan";
console.log(b) // rocyuan
```

### 字面量类型

```typescript
// 赋值必须与字面量的类型一致
let a: "roc" = "roc";
let b: 123 = 123;
// 一般结合联合类型使用
let c: "right" | "left" | "top" | "bottom" = "top"
```

## 函数详解

### 函数类型

```typescript
// 1. function定义函数的类型
function add(a: number, b: number): number {
	return a + b;
}

// 2. 函数作为 参数 的类型
function fn1(fn: () => void) {
  fn()
}
function fn2() {
  console.log("我是fn2")
}
fn1(fn2)

// 3. 函数作为 变量 的类型
// 注意：定义类型的函数参数名字可以不同，但是不能省略
type TypeFn = (a1: string) => string
let fn: TypeFn = (a: string) => {
  return a;
}
console.log(fn("rocyuan"))

```

### 参数可选

结合可选类型

```typescript
// 注意：可选类型必须写到必选类型后面
function fn(a: string, b?: string){
}
```

### 参数的默认值

属于ES6的知识点

```typescript
function fn(a: number, b: number = 666){
	console.log(a, b)
}
fn(20)

function fn(a: number = 666, b: number){
	console.log(a, b)
}
fn(666, 20) // 要么传默认值
fn(undefined, 20) // 要么传undefined
```

### 函数的剩余参数

```typescript
function add(...nums: number[]): number {
  let sum: number = 0;
	nums.forEach((item) => {
  	sum += item
  })
  return sum
}
add(1, 2, 3, 4);
```

### 函数的重载

```typescript
// 重载方法类型
function add(a: number, b: number): number;
function add(a: string, b: string): string;

// 重载方法的实现（重载方法的实现不能直接调用）
function add(a: any, b: any): any {
	return a + b;
}

let res1 = add(1, 2);
let res2 = add("roc", "yuan");
console.log(res1, res2);
```

## 类 class

### 修饰符

#### public

在所有类都可访问

```typescript
class Roc{
	public name: string = "rocyuan"
}
```

#### private

只在当前类中能访问

```typescript
class Roc{
	private name: string = "rocyuan"
}
```

#### protected

在类中和子类中可访问

```typescript
class Roc{
	protected name: string = "rocyuan"
}
```

#### readonly

只读的  可以在构造器中赋值，赋值后不可修改

```typescript
class Roc{
	readonly name: string = "rocyuan"
}
```

### 访问器 get set

```typescript
class Roc{
	private _name: string;
  constructor(name: string) {
  	this._name = name;
  }
  
  // setter
  set name(newName) {
  	this._name = newName;
  }
  // getter
  get name() {
  	return this._name;
  }
}

const roc: Roc = new Roc("roc");

roc.name = "rocyuan";
console.log(roc.name);
```

### 静态成员 static

可以通过类本身访问

```typescript
class Roc{
	static name: string = "rocyaun"
}
console.log(Roc.name)
```

### 抽象类 abstract

抽象方法必须存在于抽象类里面，抽象类不能被实例化，抽象方法必须被子类实现。

```typescript
// 实现不管传入什么图形都能计算出面积
// !!! 这里的any类型很不严谨 !!! 什么类型的都能传
/*
function makeArea(shape: any) {
	return shape.getArea()
}
*/

// 将抽象类作为shape参数的 类型，可以避免使用者乱传其他类型参数，也可以避免传入new Shape()
function makeArea(shape: Shape) {
	return shape.getArea()
}

// 定义抽象类 抽象方法
// 为了避免给makeArea传入new Shape(), 所以将Shape类定义成抽象类，抽象类不可以被实例化
abstract class Shape {
  // 抽象方法不能有实现体，但是必须被子类实现
	abstract getArea();
} 

// 矩形
class Rectangle extends Shape {
	private width: number
  private height: number
  constructor(width: number, height: number) {
    super()
  	this.width = width;
    this.height = height;
  }
  
  getArea() {
  	return this.width * this.height;
  }
}

// 圆形
class Circle extends Shape {
	private r: number
  constructor(r: number) {
    super()
  	this.r = r;
  }
  
  getArea() {
  	return this.r * this.r * 3.14;
  }
}

console.log(makeArea(new Rectangle(3, 4)))
console.log(makeArea(new Circle(3)))
```

### 继承 extends

继承只能单继承（继承一个类）

```typescript
class Roc extends RocYuan {
}
```

## 接口 interface

### 接口声明

```typescript
interface IInfo {
	name: string
  age: number
  readonly height?: number
}
const info: IInfo = {
	name: "rocyuan",
  age: 18
}
```

### 索引类型

```typescript
interface IInfo {
	[index: number]: string
}
const info: IInfo = {
	0: "字符串",
  1: "字符串",
  2: "字符串"
}
```

### 函数类型

```typescript
interface IFn {
	(a: number): number
}

const fn: IFn = (a: number) => {
	return a;
}
```

### 接口继承

```typescript
interface IFn1 {
	getName: () => string
}
interface IFn2 {
	getAge: () => number
}

interface IFn3 extends IFn1, IFn2 {
	getHeight: () => number
}

const roc: IFn3 = {
	getName(){
  	return "rocyuan"
  },
  getAge() {
  	return 18
  },
  getHeight() {
  	return 188
  }
}
console.log(roc.getName())
console.log(roc.getAge())
console.log(roc.getHeight())
```

### 接口实现

一个类是可以实现多个接口，用","分割；继承只能继承一个（单继承）

```typescript
interface IStudent1 {
	name: string
  age: number
  running: () => void
}
interface IStudent2 {
  height: number
}
class Student implements IStudent1, IStudent2 {
	name = "rocyuan"
  age = 18
  height = 188
  running() {
  	console.log("跑")
  }
}

const roc = new Student();
roc.running()
```

### 交叉类型（合并类型）

```typescript
interface IFn1 {
	getName: () => string
}
interface IFn2 {
	getAge: () => number
}
type TFn3 = IFn1 & IFn2

const fn: TFn3 = {
	getName() {
  	return "rocyuan"
  },
  getAge() {
  	return 18
  }
}
console.log(fn.getName())
console.log(fn.getAge())
```

### interface与type的区别

interface 命名可以相同，如果名字一旦相同，则会合并定义的接口
type 是定义的别名，别名是不可以相同的

## 枚举enum

枚举类型默认的值是数字，比如我们经常用数字记录某些数据，判断数字处理逻辑，比如女，男，保密(0， 1， 2)...，使用枚举，可以大大增强代码可读性。
可简单理解为定义一常量。

```typescript
// 默认第一位是0后面的1,2,3...
enum ESex {
	GRIL,
  MALE,
  SEC
}
console.log(ESex.GRIL) // 0
console.log(ESex.MALE) // 1
console.log(ESex.SEC) // 2

/* ======================================= */

// 可以更改，比如第一位改为10，后面的是11,12,13...
enum ESex {
	GRIL = 10,
  MALE,
  SEC
}
```

## 泛型

### 认识泛型

泛型就是将类型参数化；调用者将类型以参数的形式赋值过来

### 泛型类型参数

```typescript
function roc<Type>(num: Type): Type {
	return num;
}

// 1. 明确的传入了类型
roc<number>(666);
roc<{name: "rocyuan"}>("rocyuan");

// 2. 类型推导
roc(50)
roc("roc")
```

可接受多个参数 

```typescript
function foo<T, E>(a1: T, a2: E) {
	return console.log(a1, a2);
}
foo<number, string>(666, "rocyuan")
// ts会进行类型推导
// function foo<number, string>(a1: number, a2: string): void
foo(666, "rocyuan")
```

### 泛型接口

```typescript
interface IPerson<T1 = string, T2 = number> {
	name: T1
  age: T2
}

// 没有类型推导
const roc: IPerson<string, number> = {
	name: "rocyuan",
  age: 18
}
```

### 泛型类

```typescript
class Point<T> {
	x: T
  y: T
  z: T
  constructor(x: T, y: T, z: T) {
  	this.x = x;
    this.y = y;
    this.z = z;
  }
}
const p1 = new Point<string>("12.12", "13.13", "14.14")
const p2: Point<string> = new Point("12.12", "13.13", "14.14")
// 会有类型推导
const p3 = new Point("12.12", "13.13", "14.14")
```

### 泛型的类型约束

对传入的泛型限制类型

```typescript
interface ILength {
	length: number
}
function getLength<T extends ILength>(arg: T) {
	return arg.length;
}
console.log(getLength("rocyuan"))
// getLength(123) // error number类型的没有length属性
```

## 命名空间 namespace

最早期的时候叫内部模块，js没有模块化时候会使用，现在使用较少。

```typescript
// 同一文件中：

export namespace roc1 {
	export function format() {
  	return "2020-02-02"
  }
}
export namespace roc2 {
	export function format() {
  	return "22.22"
  }
}
  
roc1.format()
roc2.format()

// 不同文件（需要导出namespace）
import {roc1, roc2} from "xxx"
roc1.format()
roc2.format()

```

## ts对类型的管理与查找规则（.d.ts文件，@types/xxx仓库）

文件后缀名为 .ts 是编写ts代码的最终会输出js代码文件。
文件后缀名为 .d.ts 是类型声明文件用来做类型检测的，它仅仅用来做类型检测，告知ts我们有哪些类型。
有的第三方库没有.d.ts声明文件引入后就会报错

### 内置类型声明

内置类型都是ts自带的

### 外部声明文件（第三方库类型声明）

1. 下载第三方库时候第三方库里面有 .d.ts ；正常使用即可
2. Ts社区维护的类型声明仓库：[https://github.com/DefinitelyTyped/DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)，用npm安装：@types/xxx，比如react就有：@types/react；查询自己所使用的第三方库在这个仓库中有没有类型声明文件:[https://www.typescriptlang.org/dt/search?search=](https://www.typescriptlang.org/dt/search?search=)，如果这里还没有那就得自己写了。

### 自定义声明文件

自己编写声明文件，新建xxx.d.ts，ts会自动识别

```typescript
/* =============== xxx.d.ts文件 ============== */
// 声明模块
declare module 'lodash' {
  // 不在这里声明join，下面文件使用_.join会报错
	export function join(arr: any[]): void
}
// 声明 变量、函数...
declare let name: string
declare function roc(): void
// 声明文件
declare module '*.jpg'
declare module '*.png'
// 声明命名空间（相当于全局变量）
declare namespace ${
	export function ajax(settings: any): any
}

/* =============== 使用lodash的文件 ============== */
import _ from "lodash";
import roc from "xxx/xx.jpg";
_.join(["aaa", "bbb"])
  
$.ajax({})
```
