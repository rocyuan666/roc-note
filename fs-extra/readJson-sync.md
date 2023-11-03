# readJsonSync(file[, options])

读取JSON文件，然后将其解析为对象。

**Alias:** `readJSONSync()`

- `file` `<String>`
- `options` `<Object>` (与 `[jsonFile.readFileSync()](https://github.com/jprichardson/node-jsonfile#readfilesyncfilename-options)`[ options](https://github.com/jprichardson/node-jsonfile#readfilesyncfilename-options)一样)

## Example:

```javascript
const fs = require('fs-extra')

const packageObj = fs.readJsonSync('./package.json')
console.log(packageObj.version) // => 2.0.0
```

---

readJsonSync（）可以接受设置为false的throws选项，如果JSON无效，则不会引发。
 Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/some-invalid.json'
const data = '{not valid JSON'
fs.writeFileSync(file, data)

const obj = fs.readJsonSync(file, { throws: false })
console.log(obj) // => null
```
