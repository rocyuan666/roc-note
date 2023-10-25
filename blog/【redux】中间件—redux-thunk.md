redux使用dispatch派发action会触发reducer，但是有时候我们需要dispatch一个action之后，到达reducer之前，进行一些额外的操作（一般请求异步数据），就需要用到中间件（middleware）。中间件就是对dispatch()的增强。
## redux-thunk原理
redux-thunk让store.dispatch方法不只接受一个对象，也可以接受一个函数，它内部做了处理，如果这个接收到的是一个函数，就执行它（可在这个函数里做异步操作），如果不是，就按照原来的dispatch执行。
## redux-thunk使用
安装: yarn add redux-thunk
使用redux中提供的applyMiddleware方法可以将所有中间件组成一个数组，依次执行（这里只用redux-thunk中间件）。现在就已经完成了dispatch()的功能增强。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840449841-20e110d1-8bcb-4bc5-91dd-da6a9b597d8f.png#clientId=uf2e6246a-908d-4&from=paste&id=u8f3e4823&originHeight=393&originWidth=717&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ud7881f2b-74da-4581-9c30-6a228ee5539&title=)
不管我们使用不使用中间件需要更改store中的state都要经过action，定义好action；再定义dispatch接收的那个函数（也就是redux-thunk帮我们执行的函数，函数接收一个dispatch），在此函数中进行我们的异步操作，操作完成后再去dispatch派发action改变state（此时派发，接收的是一个action对象，所以与原生dispatch运行一致）。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840450719-13912f04-c886-457a-bad8-6cb4e9cc4b40.png#clientId=uf2e6246a-908d-4&from=paste&id=uc7f897de&originHeight=390&originWidth=511&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ud9908f41-3f36-4d98-8c4c-6acc065670a&title=)
此时我们还没有dispatch派发getBannerData函数
在组件中配合react-redux派发getBannerData函数。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840450308-4e7964d4-7cde-4a7f-8e35-f324b0449c77.png#clientId=uf2e6246a-908d-4&from=paste&id=u287d5e10&originHeight=678&originWidth=563&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u7c75dff1-e663-4e23-ab94-15d32dd74e6&title=)
整个redux-thunk流程就是这样。
## 示例结果
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840450878-8456bf67-4081-4be2-b11f-b561e82df42a.png#clientId=uf2e6246a-908d-4&from=paste&id=u8f53bfa4&originHeight=646&originWidth=632&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u1baa3763-7781-432c-b842-7326367271d&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840453722-6746fde8-562e-4e20-933d-0f9eb2139553.png#clientId=uf2e6246a-908d-4&from=paste&id=u60770b5f&originHeight=600&originWidth=745&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u6f4edbb4-37d9-45a7-b6f2-9d796808bb4&title=)
