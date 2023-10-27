# 按比例缩放方案

个人常用，原理是css3缩放属性
已封装为组件发布至npm（vue2、vue3两种版本）
[https://www.npmjs.com/package/vue2-scale-box](https://www.npmjs.com/package/vue2-scale-box)
[https://www.npmjs.com/package/vue3-scale-box](https://www.npmjs.com/package/vue3-scale-box)

## vue-组件方案

```vue
<template>
  <div
    class="ScaleBox"
    ref="ScaleBox"
    :style="{
      width: width + 'px',
      height: height + 'px',
    }"
  >
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "ScaleBox",
  props: {},
  data() {
    return {
      scale: 0,
      width: 1920,
      height: 1080,
    };
  },
  mounted() {
    this.setScale();
    window.addEventListener("resize", this.debounce(this.setScale));
  },
  methods: {
    getScale() {
      // 固定好16：9的宽高比，计算出最合适的缩放比
      const { width, height } = this;
      const wh = window.innerHeight / height;
      const ww = window.innerWidth / width;
      return ww < wh ? ww : wh;
    },
    setScale() {
      // 获取到缩放比例，设置它
      this.scale = this.getScale();
      if (this.$refs.ScaleBox) {
        this.$refs.ScaleBox.style.setProperty("--scale", this.scale);
      }
    },
    debounce(fn, delay) {
      const delays = delay || 100;
      let timer;
      return function () {
        const th = this;
        const args = arguments;
        if (timer) {
          clearTimeout(timer);
        }
        timer = setTimeout(function () {
          timer = null;
          fn.apply(th, args);
        }, delays);
      };
    },
  },
};
</script>

<style lang="scss">
#ScaleBox {
  --scale: 1;
}
.ScaleBox {
  position: absolute;
  transform: scale(var(--scale)) translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  transform-origin: 0 0;
  left: 50%;
  top: 50%;
  transition: 0.3s;
  z-index: 999;
  background: rgba(255, 0, 0, 0.3);
}
</style>

```

## vue-mixins方案

```javascript
// 屏幕适配 mixin 函数
// * 默认缩放值
const scale = {
  width: "1",
  height: "1",
};

// * 设计稿尺寸（px）
const baseWidth = 1920;
const baseHeight = 1080;

// * 需保持的比例（默认1.77778）
const baseProportion = parseFloat((baseWidth / baseHeight).toFixed(5));

export default {
  data() {
    return {
      // * 定时函数
      drawTiming: null,
      isScale: true, //是否进行全局适配
    };
  },
  mounted() {
    if (!this.isScale) {
      return;
    }
    this.calcRate();
    window.addEventListener("resize", this.resize);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.resize);
  },
  methods: {
    calcRate() {
      /*
        给最外层起ref！！！
      */
      const appRef = this.$refs["appRef"];
      if (!appRef) return;
      // 当前宽高比
      const currentRate = parseFloat((window.innerWidth / window.innerHeight).toFixed(5));
      if (appRef) {
        if (currentRate > baseProportion) {
          // 表示更宽
          scale.width = ((window.innerHeight * baseProportion) / baseWidth).toFixed(5);
          scale.height = (window.innerHeight / baseHeight).toFixed(5);
          appRef.style.transform = `scale(${scale.width}, ${scale.height}) translate(-50%, -50%)`;
        } else {
          // 表示更高
          scale.height = (window.innerWidth / baseProportion / baseHeight).toFixed(5);
          scale.width = (window.innerWidth / baseWidth).toFixed(5);
          appRef.style.transform = `scale(${scale.width}, ${scale.height}) translate(-50%, -50%)`;
        }
      }
    },
    resize() {
      if (!this.isScale) {
        return;
      }
      clearTimeout(this.drawTiming);
      this.drawTiming = setTimeout(() => {
        this.calcRate();
      }, 200);
    },
  },
};

```

# rem

```javascript
/*
  github 大数据可视化展板通用模板 中方案
*/
$(document).ready(function () {
  var whei = $(window).width();
  $("html").css({ fontSize: whei / 20 });
  $(window).resize(function () {
    var whei = $(window).width();
    $("html").css({ fontSize: whei / 20 });
  });
});
```

# echart resize

window变化 或 DOM变化需要改变

```javascript
const myEchart = echarts.init(
  document.getElementById("xxx")
);
const option = {}
myEchart.setOption(option);
// window变化
window.addEventListener("resize", function() {
  myEchart.resize();
});
// DOM变化
new ResizeObserver(() => {
  myEchart.resize();
}).observe(this.$refs["xxx"]);
```

# 动态单位方案

定义fontSize方法

```javascript
function fontSize(res) {
  let docEl = document.documentElement,
      clientWidth =
      window.innerWidth ||
      document.documentElement.clientWidth ||
      document.body.clientWidth;
  if (!clientWidth) return;
  // 此处的3840 为设计稿的宽度，记得修改！
  let fontSize = clientWidth / 3840;
  return res * fontSize;
}
```

使用

```javascript
 legend: [
    {
      data: ["人数"],
      top: fontSize(10),
      right: fontSize(320),
      itemWidth: fontSize(14),
      textStyle: {
        color: "#fff",
        fontSize: fontSize(20),
      },
    },
]
```

窗口发生变化重绘图表

```javascript
// 添加窗口大小改变监听事件，当窗口大小改变时，图表会重新绘制，自适应窗口大小
window.addEventListener("resize", function() {
  chart.resize();
});
```
