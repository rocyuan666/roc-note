在class组件中我们触发事件，比如点击事件后想拿到state，第一反应肯定是点击后用this.state拿数据
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326602-7c733eb7-2c20-46ab-adfb-c81415becc1e.png#clientId=u05cf078f-3cf6-4&from=paste&id=u439ee0d9&originHeight=515&originWidth=470&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u92d55cfd-d6e5-4395-957c-6a9d252ba65&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326022-ac5f8911-70b6-49da-b9b2-857cd90998c7.png#clientId=u05cf078f-3cf6-4&from=paste&id=u5a679c1e&originHeight=254&originWidth=617&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u3080bb3a-68b9-49bf-9c5c-d4504c9ea2a&title=)
但是，很遗憾react中这样是拿不到的，直接报错，打印this竟然是undefined
react官方:
在JSX回调中你必须注意 this 的指向。 在 JavaScript 中，类方法默认没有绑定的。如果你忘记绑定 this.handleClick 并将其传递给onClick，那么在直接调用该函数时，this 会是 undefined 。
## 解决的方法
我这里列举常见的两种解决的方法，一种是用bind方法解决，一种是箭头函数；而bind方法写法有两种方案。
### bind—直接在事件赋值的函数处绑定this
用bind方法为事件处理函数绑定this指向
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326444-22ff8f73-3817-4a0e-97d2-f4fbb9e40420.png#clientId=u05cf078f-3cf6-4&from=paste&id=ue3ce2826&originHeight=471&originWidth=592&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ufa79ba6c-0e86-4a39-9be1-cbfe8180241&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326155-2b1017e7-193b-4bd3-bf0b-e884658c2622.png#clientId=u05cf078f-3cf6-4&from=paste&id=u9615062d&originHeight=192&originWidth=347&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u3b74b461-dc9a-4135-b3d8-39045249625&title=)
### bind—在构造函数处将bind后的返回值再次赋值给事件处理函数
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326281-e5a4fe2d-9f47-453a-98f5-2c3e3cda4665.png#clientId=u05cf078f-3cf6-4&from=paste&id=u79540d08&originHeight=505&originWidth=492&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ueca6dae9-7726-4e77-9881-ba615a5ee92&title=)
### 箭头函数
这种写法个人还是比较喜欢的，它是点击后执行一个箭头函数（而箭头函数是不会绑定this的），再在箭头函数里执行事件处理函数并且传递参数也很方便。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840326911-e349f38d-2a1f-4d9f-9775-0bb5b78b0b6a.png#clientId=u05cf078f-3cf6-4&from=paste&id=uecfdf041&originHeight=510&originWidth=546&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uda46842f-1e71-4b8f-8dc3-5f7566705c6&title=)
