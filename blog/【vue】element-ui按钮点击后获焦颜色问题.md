采用自定义指令解决，监听获焦事件后让它失焦`v-autoBlur`

## 定义指令

```javascript
// autoBlur.js
export default {
  mounted(el) {
    el.addEventListener('focus', () => {
      el.blur()
    })
  },
}

```
```javascript
import autoBlur from '@/directive/autoBlur.js'

app.directive('autoBlur', autoBlur)
```

## 使用指令

```vue
<el-button type="primary" plain icon="Plus" @click="handleAdd" v-autoBlur>新增</el-button>
```
