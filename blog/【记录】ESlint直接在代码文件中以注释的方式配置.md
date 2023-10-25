注意：代码文件内以注释配置的规则会覆盖配置文件里的规则，优先级要更高。
可以在你的文件中使用以下格式的块注释来临时禁止规则出现警告：
```javascript
/* eslint-disable */
alert('foo');
/* eslint-enable */
```
你也可以对指定的规则启用或禁用警告:
```javascript
/* eslint-disable no-alert, no-console */
alert('foo');console.log('bar');
/* eslint-enable no-alert, no-console */
```
如果在整个文件范围内禁止规则出现警告，将/* eslint-disable */ 块注释放在文件顶部：
```javascript
/* eslint-disable */
alert('foo');
```
你也可以对整个文件启用或禁用警告:
```javascript
/* eslint-disable no-alert */
// Disables no-alert for the rest of the file
alert('foo');
```
可以在你的文件中使用以下格式的行注释在某一特定的行上禁用所有规则：
```javascript
alert('foo'); 
// eslint-disable-line
// eslint-disable-next-linealert('foo');
```
在某一特定的行上禁用某个指定的规则：
```javascript
alert('foo'); 
// eslint-disable-line no-alert
// eslint-disable-next-line no-alertalert('foo');
```
在某个特定的行上禁用多个规则：
```javascript
alert('foo');
// eslint-disable-line no-alert, quotes, semi
// eslint-disable-next-line no-alert, quotes, semialert('foo');
```
上面的所有方法同样适用于插件规则。例如，禁止eslint-plugin-example的 rule-name规则，把插件名（example）和规则名（rule-name）结合为 example/rule-name：
```javascript
foo(); // eslint-disable-line example/rule-name
```
注意：为文件的某部分禁用警告的注释，告诉 ESLint 不要对禁用的代码报告规则的冲突。ESLint 仍解析整个文件，然而，禁用的代码仍需要是合法的 JavaScript 语法。
