Vue Router 个人常用整理
完整官方文档：
[https://router.vuejs.org/zh](https://router.vuejs.org/zh/)

## 路由安装与导入
```javascript
安装：
npm install vue-router --save
导入：
import VueRouter from 'vue-router'
```
## 路由基本使用
### 1.配置路由映射关系之前需准备
```javascript
1）注册
Vue.use(VueRouter)
2）创建vue-router实例对象
const router = new VueRouter({
  routes  //路由映射配置
})
3）将router对象传入Vue实例中(在main.js中导入，传入Vue实例中)
export default router
```
### 2.配置路由映射
```javascript
1）创建路由组件
创建所需要转跳的.vue组件，比如创建Home.vue和Profile.vue
2）配置映射关系
import Home from '/components/Home'
import Profile from '/components/Profile'
const routes = [
  {
    path: '/home',
    component: Home
  },
  {
    path: '/profile',
    component: Profile
  }
]
3）使用路由
<router-view></router-view>
<router-link to="/home"></router-link>
<router-link to="/profile"></router-link>
```
### 3.路由重定向（redirect）使用
```javascript
const routes = [
  {
    path: '/'
    redirect: '/home'
  },
  {
    path: '/home',
    component: Home
  },
  {
    path: '/profile',
    component: Profile
  }
]
```
### 4.router-link属性
```javascript
1）tag="button"（默认渲染为a标签）
2）replace 禁止浏览器返回按钮（默认可以返回）
3）active-class="active" （更改活跃状态class，默认为“router-link-active”）
```
### 5.不用router-link，使用代码转跳
```javascript
可以点击浏览器的返回按钮:
this.$router.push('/home')
不可以点击浏览器的返回按钮:
this.$router.replace('/home')
```
### 6.实例router对象时常用配置
```javascript
const router = new VueRouter({
  routes,  //路由映射配置
  mode: history,  //更改默认的“哈希模式”为“history模式”,哈希模式的路径有#号
  newVueRouter: 'active'  //更改活跃状态class
})
```
## 动态路由
动态路由官网文档：
[https://router.vuejs.org/zh/guide/essentials/dynamic-matching.html](https://router.vuejs.org/zh/guide/essentials/dynamic-matching.html)
```javascript
const routes = [
  {
    path: '/profile:userName',
    component: Profile
  }
]

toProfile(){
  // 1.跳转携带数据
  tihs.$router.push('/profile/zhangshan')
}

// 2.profile.vue中拿到userName（注意是$route不是$router）：
this.$route.params.userName
```
$router与$route区别？
$router：new出来的VueRouter
$route：处于活跃的那个路由
## 路由参数传递
官方文档：
[https://router.vuejs.org/zh/guide/essentials/passing-props.html](https://router.vuejs.org/zh/guide/essentials/passing-props.html)
```javascript
1. params的类型（以上方式）：动态路由方式（this.$route.params.userName）
2. query的类型：(this.$route.query.userName)

query方式：
toProfile(){
  // 1.跳转
  this.$router.push({
    path: '/profile',
    query: {
      userName: 'zhangsan'
    }
  })
}
2. profile.vue中拿数据
this.$route.query.userName
```
## 路由嵌套使用(children)
```javascript
const routes = [
  {
    path: '/home',
    component: Home,
    children: [
      {
      path: 'news',
      component: News
      }
    ]
  }
]

路由映射配置中:children: []
Home组件中:<router-link to='/home/news'><router-view/>
```
## keep-alive
keep-alive所包裹的动态组件会被缓存，当离开某个组件，不会让组件频繁创建销毁
```javascript
<keep-alive exclude="name(组件的name属性值)">
  <router-view></router-view>
</keep-alive>

keep-alive属性:
include: 字符串或正则，只有匹配的会被缓存
exclude: 字符串或正则，匹配的不会被缓存

keep-alice包裹的组件转跳会触发一下钩子方法，没有keep-alice,以下两方法不会生效
activated：是在被包裹组建被激活的状态下使用的生命周期钩子
deactivated：在被包裹组件停止使用时调用
```
## 路由懒加载
官方文档：
[https://router.vuejs.org/zh/guide/advanced/lazy-loading.html](https://router.vuejs.org/zh/guide/advanced/lazy-loading.html)
```javascript
常用：
const Home = () => import("/components/Home")
```
## 导航守卫
官方文档：
[https://router.vuejs.org/zh/guide/advanced/navigation-guards.html](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html)
```javascript
举个栗子：使用beforeEach改变页面title
{
  path: '/home',
  component: Home,
  路由独享守卫
  beforeEnter: function(to, from, next){
    next()
  }
  meta: {
    title: '首页'
  }
}

前置钩子（回调）******全局守卫******
router.beforeEach(function(to, from, next){
  //路由嵌套出现错误
  //document.title = to.meta.title
  //正确的
  document.title = to.matched[0].meta.title
  next()
})

meta： 元数据：描述数据的数据
beforeEach ：前置守卫：跳转之前执行
afterEach：后置钩子：跳转完成后执行（function（to, from））,没有next，因为跳转完成了
```
