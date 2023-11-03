# About `fs.read()` & `fs.write()`

`[fs.read()](https://nodejs.org/api/fs.html#fs_fs_read_fd_buffer_offset_length_position_callback)`, `[fs.write()](https://nodejs.org/api/fs.html#fs_fs_write_fd_buffer_offset_length_position_callback)`, & `[fs.writev()](https://nodejs.org/api/fs.html#fs_fs_writev_fd_buffers_position_callback)` 与其他fs方法的不同之处在于，它们的回调是用3个参数而不是通常的2个参数调用的。

如果您将它们与回调一起使用，它们将照常工作。然而，它们的promise用法有点不同。fs extra承诺这些方法，如`[util.promisify()](https://nodejs.org/api/util.html#util_util_promisify_original)`（仅在Node 8+中可用）。

以下是promise用法示例：

## `fs.read()`

```javascript
// 使用 Promise:
fs.read(fd, buffer, offset, length, position)
  .then(results => {
    console.log(results)
    // { bytesRead: 20, buffer: <Buffer 0f 34 5d ...> }
  })

// 使用 async/await:
async function example () {
  const { bytesRead, buffer } = await fs.read(fd, Buffer.alloc(length), offset, length, position)
}
```

## `fs.write()`

```javascript
// 使用 Promise:
fs.write(fd, buffer, offset, length, position)
  .then(results => {
    console.log(results)
    // { bytesWritten: 20, buffer: <Buffer 0f 34 5d ...> }
  })

// 使用 async/await:
async function example () {
  const { bytesWritten, buffer } = await fs.write(fd, Buffer.alloc(length), offset, length, position)
}
```

## `fs.writev()`

```javascript
// 使用 async/await:
async function example () {
  const { bytesWritten, buffers } = await fs.writev(fd, buffers, position)
}
```
