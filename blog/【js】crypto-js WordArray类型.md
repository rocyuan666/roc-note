wordArray，我把它理解成CryptoJS中定义的 新的 数据类型，叫“单词数组”。
```javascript
import CryptoJS from "crypto-js";

// 创建一个空的 WordArray对象
const wordArray = CryptoJS.lib.WordArray.create();
```
# 转换
## WordArray对象 转 16进制字符串
```javascript
// 默认CryptoJS.enc.Hex，即16进制字符串
const string = wordArray.toString();
// utf-8字符串
const string = wordArray.toString(CryptoJS.enc.Utf8);
```
## 16进制字符串 转 WordArray对象
```javascript
const wordArray = CryptoJS.enc.Hex.parse(hexString);
```
## WordArray对象 转 utf8字符串
```javascript
const utf8String = CryptoJS.enc.Utf8.stringify(wordArray);
//等价于
wordArray.toString(CryptoJS.enc.Utf8);
```
## utf8字符串 转 WordArray对象
```javascript
const wordArray = CryptoJS.enc.Utf8.parse(utf8String);
```
## WordArray对象 转 Base64字符串
```javascript
const base64String = CryptoJS.enc.Base64.stringify(wordArray);
```
## Base64字符串 转 WordArray对象
```javascript
const wordArray = CryptoJS.enc.Base64.parse(base64String);
```
