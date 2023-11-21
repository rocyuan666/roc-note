为播放m3u8地址需求封装的组件，参数选项如果不够参考官网属性修改  
官网配置选项地址：[https://videojs.com/guides/options/](https://videojs.com/guides/options/)

`RocVideojs.vue`  
```vue
<template>  
    <video class="video-js" ref="myPlayerRef" :poster="fullPoster"></video>  
</template>  
  
<script setup name="RocVideojs">  
import { computed, ref } from 'vue'  
import videojs from 'video.js'  
import zhCn from 'video.js/dist/lang/zh-CN.json'  
import 'video.js/dist/video-js.min.css'  
  
videojs.addLanguage('zh-CN', zhCn)  
  
const props = defineProps({  
    src: {  
        type: String,  
        default: '',  
    },  
    type: {  
        type: String,  
        default: 'application/x-mpegURL',  
    },  
    poster: {  
        type: String,  
        default: '',  
    },  
    controls: {  
        type: Boolean,  
        default: true,  
    },  
    autoplay: {  
        type: Boolean,  
        default: true,  
    },  
    width: {  
        type: [String, Number],  
        default: 640,  
    },  
    height: {  
        type: [String, Number],  
        default: 360,  
    },  
})  
  
const fullPoster = computed(() => (props.poster ? import.meta.env.VITE_APP_BASE_API + props.poster : ''))  
const myPlayerRef = ref(null)  
let myPlayer = null  
  
/**  
 * 初始化播放器  
 */  
function initVideojs() {  
    const options = {  
        controls: props.controls,  
        //自动播放属性 false true muted play any        autoplay: props.autoplay ? 'any' : false,  
        preload: 'auto',  
        width: props.width,  
        height: props.height,  
        sources: [  
            {  
                src: props.src,  
                type: props.type,  
            },  
        ],  
    }  
    myPlayer = videojs(myPlayerRef.value, options, function () {  
        videojs.log('播放器准备好了')  
    })  
}  
  
/**  
 * 播放  
 */  
function play() {  
    if (myPlayer) myPlayer.play()  
}  
  
/**  
 * 暂停播放  
 */  
function pause() {  
    if (myPlayer) myPlayer.pause()  
}  
  
/**  
 * 卸载播放器  
 */  
function dispose() {  
    if (myPlayer) myPlayer.dispose()  
}  
  
defineExpose({  
    init: initVideojs,  
    play,  
    pause,  
    dispose,  
})  
</script>  
  
<style scoped lang="scss"></style>
```

使用：

如果在弹窗中并且播放的是推流地址类型（m3u8），关闭弹窗需要调用 `dispose` 方法销毁掉videojs对象，否则推流地址不会停；调用 `dispose` 方法后会发生打开第一次弹窗正常运行，点击第二次报错，是因为 `dispose` 方法会删除掉 video dom元素，再次打开就会找不到 video 元素；在 `RocVideojs` 组件使用 `v-if` 处理每次打开弹窗都重新创建该组件dom即可（或者在 `el-dialog` 上加上 `destroy-on-close` 属性）。

`cam.vue`  
```vue
<template>  
    <el-dialog :title="title" v-model="open" width="1200" append-to-body :close-on-click-modal="false" @closed="handleClosed">  
        <RocVideojs v-if="open" ref="rocVideoRef" :poster="rowInfo.img_url" :src="rowInfo.video_url" width="1120" height="630"></RocVideojs>  
    </el-dialog></template>  
  
<script setup name="Cam">  
import { ref, getCurrentInstance, nextTick } from 'vue'  
import RocVideojs from '@/components/RocVideojs'  
  
const { proxy } = getCurrentInstance()  
  
const title = ref('')  
const open = ref(false)  
const rowInfo = ref({})  
  
/**  
 * 打开对话框  
 * @param row  
 */  
function handleOpen(row) {  
    rowInfo.value = row  
    title.value = row.name  
    open.value = true  
    nextTick(() => {  
        proxy.$refs['rocVideoRef'].init()  
    })  
}  
  
/**  
 * 关闭对话框以后  
 */  
function handleClosed() {  
    proxy.$refs['rocVideoRef'].dispose()  
}  
  
defineExpose({ handleOpen })  
</script>  
  
<style scoped lang="scss"></style>
```