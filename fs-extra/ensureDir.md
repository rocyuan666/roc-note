# ensureDir(dir[,options][,callback])

确保目录存在。如果目录结构不存在，将创建它。

**Aliases:** `mkdirs()`, `mkdirp()`

- `dir` `<String>`
- `options` `<Integer> | <Object>` 
   - 如果为整数，则为模式。
   - 如果它是Object，它将是｛mode:＜Integer＞｝。
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const dir = '/tmp/this/path/does/not/exist'
const desiredMode = 0o2775
const options = {
  mode: 0o2775
}

// 使用回调：
fs.ensureDir(dir, err => {
  console.log(err) // => null
  // dir现在已经创建，包括它要放置的目录
})

// 带有回调和模式整数
fs.ensureDir(dir, desiredMode, err => {
  console.log(err) // => null
  // 现在已经使用模式0o2775创建了dir，包括它要放置的目录
})

// 使用 Promise:
fs.ensureDir(dir)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用Promise和模式整数：
fs.ensureDir(dir, desiredMode)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (directory) {
  try {
    await fs.ensureDir(directory)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}
example(dir)

// 使用async/await和一个选项对象，包含模式：
async function exampleMode (directory) {
  try {
    await fs.ensureDir(directory, options)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}
exampleMode(dir)
```
