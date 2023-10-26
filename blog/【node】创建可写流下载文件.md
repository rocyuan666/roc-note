使用axios请求文件数据指定`responseType`

```javascript
const fs = require("fs");
const path = require("path");
const axios = require("axios");

const savePath = path.resolve(__dirname)
const writeStream = fs.createWriteStream(savePath);

axios({
	url: "https://xxxxxxxxx",
	method: "GET",
    responseType: "stream",
}).then((res) => {
	res.data.pipe(writeStream)
})
```
