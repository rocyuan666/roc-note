在定义的filters里无法拿到this。
根据官方文档可知道，过滤器传入的参数将从第二个形参开始，那么就可以通过过滤器传参实现。
在data方法返回的对象中定义that赋值this（data中可以访问到this），在使用过滤器时候将that(this)作为参数传入，那么过滤器内即可拿到that(this)。

示例：

```vue
<template>
	<div>
    <p>{{ orderDetails.paymentStatus | paymentStatus(that) }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      that: this,
      orderDetails:{}
    }
  },
  filters: {
    paymentStatus(value, that) {
      // 直接拿this是不行的，可以通过过滤器传参的方式间接拿到this
      if (value == 'payment') {
        return that.locales.DingDanXiangQing.YiZhiFu
      } else if (value == 'unpayment') {
        return that.locales.DingDanXiangQing.WeiZhiFu
      } else if (value == 'refund') {
        return that.locales.DingDanXiangQing.YiTuiKuan
      } else {
        return ''
      }
    }
  }
}
</script>
```

