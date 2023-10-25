自己在iconfont上下载的图标需要先加上iconfont（或者自己定义的）类名，再加上图标名才能显示图标。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667551867147-c9177677-514b-44f3-bef2-df54c4c40a67.png#clientId=ub303f269-92b1-4&from=paste&height=256&id=ub8fdfbda&originHeight=256&originWidth=514&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20285&status=done&style=none&taskId=ub12a9a62-c361-4b70-af94-62cf1a7c5be&title=&width=514)
修改iconfont.css中的css选择器即可
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667551906656-22e2c6f9-ecf0-4596-b483-5443b645a222.png#clientId=ub303f269-92b1-4&from=paste&height=208&id=ub8169ea8&originHeight=208&originWidth=247&originalType=binary&ratio=1&rotation=0&showTitle=false&size=7770&status=done&style=none&taskId=u8b5a804a-81c4-4f70-b8f3-6277cc34768&title=&width=247)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667552137406-6873ce87-e88d-43d1-a32d-29fd149d0122.png#clientId=ub303f269-92b1-4&from=paste&height=455&id=u1a2fe00a&originHeight=455&originWidth=766&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36537&status=done&style=none&taskId=u991f99b1-580f-4ac9-be72-a2086796c0b&title=&width=766)
```javascript
// 之前是".iconfont"; 修改为class包含"roc-icon-"字符的元素
[class*="roc-icon-"] {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```
