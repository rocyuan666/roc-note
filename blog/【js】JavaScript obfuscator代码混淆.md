## JavaScript obfuscator

JavaScript obfuscator 是一款功能强大的免费JavaScript混淆处理程序，包含多种功能，可为源代码提供保护。

github：[https://github.com/javascript-obfuscator/javascript-obfuscator](https://github.com/javascript-obfuscator/javascript-obfuscator)

## 构建工具插件

常用webpack与rollup的插件

- Webpack plugin: [webpack-obfuscator](https://github.com/javascript-obfuscator/webpack-obfuscator)
- Webpack loader: [obfuscator-loader](https://github.com/javascript-obfuscator/obfuscator-loader)
- Rollup: [rollup-plugin-javascript-obfuscator](https://github.com/javascript-obfuscator/rollup-plugin-javascript-obfuscator)
- Gulp: [gulp-javascript-obfuscator](https://github.com/javascript-obfuscator/gulp-javascript-obfuscator)
- Grunt: [grunt-contrib-obfuscator](https://github.com/javascript-obfuscator/grunt-contrib-obfuscator)
- Weex: [weex-devtool](https://www.npmjs.com/package/weex-devtool)
- Malta: [malta-js-obfuscator](https://github.com/fedeghe/malta-js-obfuscator)
- Netlify plugin: [netlify-plugin-js-obfuscator](https://www.npmjs.com/package/netlify-plugin-js-obfuscator)

## 选项

```javascript
{
  compact: true,
  controlFlowFlattening: false,
  controlFlowFlatteningThreshold: 0.75,
  deadCodeInjection: false,
  deadCodeInjectionThreshold: 0.4,
  debugProtection: false,
  debugProtectionInterval: 0,
  disableConsoleOutput: false,
  domainLock: [],
  domainLockRedirectUrl: 'about:blank',
  forceTransformStrings: [],
  identifierNamesCache: null,
  identifierNamesGenerator: 'hexadecimal',
  identifiersDictionary: [],
  identifiersPrefix: '',
  ignoreImports: false,
  inputFileName: '',
  log: false,
  numbersToExpressions: false,
  optionsPreset: 'default',
  renameGlobals: false,
  renameProperties: false,
  renamePropertiesMode: 'safe',
  reservedNames: [],
  reservedStrings: [],
  seed: 0,
  selfDefending: false,
  simplify: true,
  sourceMap: false,
  sourceMapBaseUrl: '',
  sourceMapFileName: '',
  sourceMapMode: 'separate',
  sourceMapSourcesMode: 'sources-content',
  splitStrings: false,
  splitStringsChunkLength: 10,
  stringArray: true,
  stringArrayCallsTransform: true,
  stringArrayCallsTransformThreshold: 0.5,
  stringArrayEncoding: [],
  stringArrayIndexesType: [
  	'hexadecimal-number'
	],
  stringArrayIndexShift: true,
  stringArrayRotate: true,
  stringArrayShuffle: true,
  stringArrayWrappersCount: 1,
  stringArrayWrappersChainedCalls: true,
  stringArrayWrappersParametersMaxCount: 2,
  stringArrayWrappersType: 'variable',
  stringArrayThreshold: 0.75,
  target: 'browser',
  transformObjectKeys: false,
  unicodeEscapeSequence: false
}
```

## 选项说明

### `compact`

Type: `boolean` Default: `true`

在一行上输出紧凑的代码。

### `config`

Type: `string` Default: ``

包含混淆器选项的JS/JSON配置文件的名称。这些将被直接传递给CLI的选项覆盖

### `controlFlowFlattening`

Type: `boolean` Default: `false`

**此选项极大地影响性能，最多可使运行时速度慢1.5倍。使用`controlFlowFlatteningThreshold`值来设置受控制流扁平化影响的节点百分比。**

启用代码控制流扁平化。控制流扁平化是一种阻碍程序理解的源代码结构转换。

Example:

```typescript
// input
(function () {
  function foo() {
    return function () {
      var sum = 1 + 2;
      console.log(1);
      console.log(2);
      console.log(3);
      console.log(4);
      console.log(5);
      console.log(6);
    };
  }

  foo()();
})();

// output
(function () {
  function _0x3bfc5c() {
    return function () {
      var _0x3260a5 = {
        WtABe: "4|0|6|5|3|2|1",
        GokKo: function _0xf87260(_0x427a8e, _0x43354c) {
          return _0x427a8e + _0x43354c;
        },
      };
      var _0x1ad4d6 = _0x3260a5["WtABe"]["split"]("|"),
        _0x1a7b12 = 0x0;
      while (!![]) {
        switch (_0x1ad4d6[_0x1a7b12++]) {
          case "0":
            console["log"](0x1);
            continue;
          case "1":
            console["log"](0x6);
            continue;
          case "2":
            console["log"](0x5);
            continue;
          case "3":
            console["log"](0x4);
            continue;
          case "4":
            var _0x1f2f2f = _0x3260a5["GokKo"](0x1, 0x2);
            continue;
          case "5":
            console["log"](0x3);
            continue;
          case "6":
            console["log"](0x2);
            continue;
        }
        break;
      }
    };
  }

  _0x3bfc5c()();
})();
```

### `controlFlowFlatteningThreshold`

Type: `number` Default: `0.75` Min: `0` Max: `1`

`controlFlowFlattening`变换将应用于任何给定节点的概率。

此设置对于大代码特别有用，因为大量的控制流转换会降低代码速度并增加代码大小。

`controlFlowFlatteningThreshold: 0` 等于 `controlFlowFlattening: false`.

### `deadCodeInjection`

Type: `boolean` Default: `false`

**显著增加混淆代码的大小(高达200%)，仅在混淆代码的大小无关紧要时使用。使用`deadCodeInjectionThreshold`设置受死代码注入影响的节点百分比。**

**该选项强制启用`stringArray`选项。**

使用此选项，随机的死代码块将被添加到混淆的代码中。

Example:

```typescript
// input
(function () {
  if (true) {
    var foo = function () {
      console.log("abc");
    };
    var bar = function () {
      console.log("def");
    };
    var baz = function () {
      console.log("ghi");
    };
    var bark = function () {
      console.log("jkl");
    };
    var hawk = function () {
      console.log("mno");
    };

    foo();
    bar();
    baz();
    bark();
    hawk();
  }
})();

// output
var _0x37b8 = [
  "YBCtz",
  "GlrkA",
  "urPbb",
  "abc",
  "NMIhC",
  "yZgAj",
  "zrAId",
  "EtyJA",
  "log",
  "mno",
  "jkl",
  "def",
  "Quzya",
  "IWbBa",
  "ghi",
];
function _0x43a7(_0x12cf56, _0x587376) {
  _0x43a7 = function (_0x2f87a8, _0x47eac2) {
    _0x2f87a8 = _0x2f87a8 - (0x16a7 * 0x1 + 0x5 * 0x151 + -0x1c92);
    var _0x341e03 = _0x37b8[_0x2f87a8];
    return _0x341e03;
  };
  return _0x43a7(_0x12cf56, _0x587376);
}
(function () {
  if (!![]) {
    var _0xbbe28f = function () {
      var _0x2fc85f = _0x43a7;
      if (_0x2fc85f(0xaf) === _0x2fc85f(0xae)) {
        _0x1dd94f[_0x2fc85f(0xb2)](_0x2fc85f(0xb5));
      } else {
        console[_0x2fc85f(0xb2)](_0x2fc85f(0xad));
      }
    };
    var _0x5e46bc = function () {
      var _0x15b472 = _0x43a7;
      if (_0x15b472(0xb6) !== _0x15b472(0xaa)) {
        console[_0x15b472(0xb2)](_0x15b472(0xb5));
      } else {
        _0x47eac2[_0x15b472(0xb2)](_0x15b472(0xad));
      }
    };
    var _0x3669e8 = function () {
      var _0x47a442 = _0x43a7;
      if (_0x47a442(0xb7) !== _0x47a442(0xb0)) {
        console[_0x47a442(0xb2)](_0x47a442(0xb8));
      } else {
        _0x24e0bf[_0x47a442(0xb2)](_0x47a442(0xb3));
      }
    };
    var _0x28b05a = function () {
      var _0x497902 = _0x43a7;
      if (_0x497902(0xb1) === _0x497902(0xb1)) {
        console[_0x497902(0xb2)](_0x497902(0xb4));
      } else {
        _0x59c9c6[_0x497902(0xb2)](_0x497902(0xb4));
      }
    };
    var _0x402a54 = function () {
      var _0x1906b7 = _0x43a7;
      if (_0x1906b7(0xab) === _0x1906b7(0xac)) {
        _0xb89cd0[_0x1906b7(0xb2)](_0x1906b7(0xb8));
      } else {
        console[_0x1906b7(0xb2)](_0x1906b7(0xb3));
      }
    };
    _0xbbe28f();
    _0x5e46bc();
    _0x3669e8();
    _0x28b05a();
    _0x402a54();
  }
})();
```

### `deadCodeInjectionThreshold`

Type: `number` Default: `0.4` Min: `0` Max: `1`

允许设置受`deadCodeInjection`影响的节点百分比。

### `debugProtection`

Type: `boolean` Default: `false`

**如果打开开发者工具，则可以冻结浏览器。**

这个选项使得几乎不可能使用开发人员工具的调试器功能(无论是在基于webkit的还是在Mozilla Firefox上)。

### `debugProtectionInterval`

Type: `number` Default: `0`

**可以冻结您的浏览器！使用风险自负。！2.6.0版本类型为`boolean`,默认`false`**

如果设置了，将使用以毫秒为单位的间隔强制控制台选项卡上的调试模式，从而使使用开发者工具的其他功能更加困难。启用`debugProtection`时生效。建议取值范围是2000 ~ 4000毫秒。
2.6.0版本的描述：如果选中，则会使用一个间隔来强制“console”选项卡上的调试模式，从而使开发人员工具的其他功能更难使用。如果启用了`debugProtection`，则有效。

### `disableConsoleOutput`

Type: `boolean` Default: `false`

**此选项全局禁用所有脚本的`console`调用**

禁用 `console.log`, `console.info`, `console.error`, `console.warn`, `console.debug`, `console.exception` 和 `console.trace` 通过用空函数替换它们。这使得调试器的使用更加困难。

### `domainLock`

Type: `string[]` Default: `[]`

**此选项不适用于`target: 'node'`**

允许只在特定的域和/或子域上运行混淆的源代码。这使得别人很难复制粘贴您的源代码并在其他地方运行。

如果源代码没有在此选项指定的域上运行，浏览器将被重定向到传递给`domainLockRedirectUrl`选项URL的地址。

##### 多个域和子域

可以将代码锁定到多个域或子域。例如，要锁定它，使代码仅在`www.example.com`上运行，请添加`www.example.com`。要使它在包括任何子域（`example.com`，`sub.example.com`）在根域上工作，请使用`.example.com`。

### `domainLockRedirectUrl`

Type: `string` Default: `about:blank`

**此选项不适用于`target: 'node'`**

如果源代码未在`domainLock`指定的域上运行，则允许将浏览器重定向到传递的URL

### `exclude`

Type: `string[]` Default: `[]`

一种文件名或globs，表示要从混淆处理中排除的文件。

### `forceTransformStrings`

Type: `string[]` Default: `[]`

启用字符串文字的强制转换，这些文字由传递的RegExp模式匹配。

**此选项只影响不应该由`stringArrayThreshold`（或将来可能的其他阈值）转换的字符串**

该选项的优先级高于`reservedStrings`选项，但没有高于条件注释的优先级。

Example:

```typescript
{
  forceTransformStrings: ["some-important-value", "some-string_d"];
}
```

### `identifierNamesCache`

Type: `Object | null` Default: `null`

该选项的主要目标是在混淆多个源/文件时使用相同的标识符名称。

目前支持两种类型的标识符：

- 全局标识符：
   - 所有全局标识符将被写入缓存;
   - 所有匹配的未声明的全局标识符将被缓存中的值替换。
- 属性标识符，仅当启用`renameProperties`选项时：
   - 所有属性标识符都将写入缓存；
   - 所有匹配的属性标识符将被缓存中的值替换。

#### Node.js API

如果传递了`null`值，则完全禁用缓存。

如果传递了一个空对象（`{}`），则启用将标识符名称写入缓存对象（`TIdentifierNamesCache`类型）。将通过`ObfuscationResult`对象的`getIdentifierNamesCache`方法调用来访问此缓存对象。

生成的缓存对象接下来可以用作`identifierNamesGenerator`选项值，用于在混淆下一个源的所有匹配标识符名称期间使用这些名称。

Example:

```typescript
const source1ObfuscationResult = JavaScriptObfuscator.obfuscate(
  `
        function foo(arg) {
           console.log(arg)
        }
        
        function bar() {
            var bark = 2;
        }
    `,
  {
    compact: false,
    identifierNamesCache: {},
    renameGlobals: true,
  }
);

console.log(source1ObfuscationResult.getIdentifierNamesCache());
/*
    { 
        globalIdentifiers: {
            foo: '_0x5de86d',
            bar: '_0x2a943b'
        }
    }
*/

const source2ObfuscationResult = JavaScriptObfuscator.obfuscate(
  `
        // Expecting that these global functions are defined in another obfuscated file
        foo(1);
        bar();
        
        // Expecting that this global function is defined in third-party package
        baz();
    `,
  {
    compact: false,
    identifierNamesCache: source1ObfuscationResult.getIdentifierNamesCache(),
    renameGlobals: true,
  }
);

console.log(source2ObfuscationResult.getObfuscatedCode());
/*
    _0x5de86d(0x1);
    _0x2a943b();
    baz();
 */
```

#### CLI

CLI有一个不同的选项`--identifier-names-cache-path`，它允许定义现有`.json`文件的路径，该文件将用于读取和写入标识符名称缓存。

如果将传递到空文件的路径，则标识符名称缓存将写入该文件。

这个具有现有缓存的文件可以再次用作`--identifier-names-cache-path`选项值，用于在混淆下一个文件的所有匹配的标识符名称时使用这些名称。

### `identifierNamesGenerator`

Type: `string` Default: `hexadecimal`

设置标识符名称生成器。

可用值：

- `dictionary`: 标识符中的`identifiersDictionary`列表
- `hexadecimal`: 标识符名称，如`_0xabc123`
- `mangled`: 短标识符名称，如 `a`, `b`, `c`
- `mangled-shuffled`: 同等与 `mangled` 但是使用混乱的字母

### `identifiersDictionary`

Type: `string[]` Default: `[]`

为`identifierNamesGenerator`:`dictionary`选项设置标识符字典。字典中的每个标识符都将在几个变体中使用，每个字符的大小写不同。因此，字典中标识符的数量应该取决于原始源代码中的标识符数量。

### `identifiersPrefix`

Type: `string` Default: `''`

为所有全局标识符设置前缀。

当您想要混淆多个文件时，请使用此选项。此选项有助于避免这些文件的全局标识符之间的冲突。每个文件的前缀应该不同。

### `ignoreImports`

Type: `boolean` Default: `false`

防止混淆`require`。在某些情况下，当运行时环境出于某种原因只需要使用静态字符串进行这些导入时，可能会有所帮助。

### `inputFileName`

Type: `string` Default: `''`

允许使用源代码设置输入文件的名称。此名称将在内部用于生成源映射。
使用NodeJS API时需要，并且`sourceMapSourcesMode`选项具有`sources`值`。

### `log`

Type: `boolean` Default: `false`

启用将信息记录到控制台

### `numbersToExpressions`

Type: `boolean` Default: `false`

启用数字转换为表达式

Example:

```typescript
// input
const foo = 1234;

// output
const foo = -0xd93 + -0x10b4 + 0x41 * 0x67 + 0x84e * 0x3 + -0xff8;
```

### `optionsPreset`

Type: `string` Default: `default`

允许设置预设选项(`options preset`)。

可用值：

- `default`;
- `low-obfuscation`;
- `medium-obfuscation`;
- `high-obfuscation`.

所有添加选项将与预设的选定选项合并。

### `renameGlobals`

Type: `boolean` Default: `false`

**此选项可能会破坏您的代码。只有当你知道它的作用时才启用它！**

使用声明启用全局变量和函数名的混淆处理。

### `renameProperties`

Type: `boolean` Default: `false`

**此选项可能会破坏您的代码。只有当你知道它的作用时才启用它！**

允许重命名属性名。所有内置DOM属性和核心JavaScript类中的属性都将被忽略。

要在该选项的安全模式和不安全模式之间切换，请使用`renamePropertiesMode`选项。

要设置重命名属性名的格式，请使用`identifierNamesGenerator`选项。

要控制重命名哪些属性，请使用`reservedNames`选项。

Example:

```typescript
// input
(function () {
  const foo = {
    prop1: 1,
    prop2: 2,
    calc: function () {
      return this.prop1 + this.prop2;
    },
  };

  console.log(foo.calc());
})();

// output
(function () {
  const _0x46529b = {
    _0x10cec7: 0x1,
    _0xc1c0ca: 0x2,
    _0x4b961d: function () {
      return this["_0x10cec7"] + this["_0xc1c0ca"];
    },
  };
  console["log"](_0x46529b["_0x4b961d"]());
})();
```

### `renamePropertiesMode`

Type: `string` Default: `safe`

**即使在 `safe` 模式，`renameProperties`选项也可能破坏你的代码。**

指定`renameProperties`选项模式：

- `safe` - 2.11.0发布后的默认行为。试图以更安全的方式重命名属性以防止运行时错误。在这种模式下，一些属性将被排除在重命名之外。
- `unsafe` - 2.11.0发布前的默认行为。以不安全的方式重命名属性，没有任何限制。

如果一个文件使用来自其他文件的属性，则使用`identifierNamesCache`选项在这些文件之间保持相同的属性名称。

### `reservedNames`

Type: `string[]` Default: `[]`

禁用标识符的混淆和生成，由传递的RegExp模式匹配。

Example:

```typescript
{
  reservedNames: ["^someVariable", "functionParameter_d"];
}
```

### `reservedStrings`

Type: `string[]` Default: `[]`

禁用由传递的RegExp模式匹配的字符串字面量的转换。

Example:

```typescript
{
  reservedStrings: ["react-native", "./src/test", "some-string_d"];
}
```

### `seed`

Type: `string|number` Default: `0`

此选项为随机生成器设置seed。这对于创建可重复的结果很有用。

如果seed是0 -随机发生器将工作没有seed。

### `selfDefending`

Type: `boolean` Default: `false`

**在使用此选项后，不要以任何方式更改被混淆的代码，因为任何像丑陋代码这样的更改都会触发自我防御，代码将不再工作!**

**此选项强制将`compact`值设置为`true`**

此选项使输出代码在格式化和变量重命名时具有弹性。如果试图在混淆的代码上使用JavaScript美化器，代码将不再工作，使其更难理解和修改。

### `simplify`

Type: `boolean` Default: `true`

通过简化实现额外的代码混淆。

**在以后的版本中，`boolean`字面值的混淆(`true` => `!![]`)将被移到这个选项下。**

Example:

```typescript
// input
if (condition1) {
  const foo = 1;
  const bar = 2;

  console.log(foo);

  return bar;
} else if (condition2) {
  console.log(1);
  console.log(2);
  console.log(3);

  return 4;
} else {
  return 5;
}

// output
if (condition1) {
  const foo = 0x1,
    bar = 0x2;
  return console["log"](foo), bar;
} else
  return condition2
    ? (console["log"](0x1), console["log"](0x2), console["log"](0x3), 0x4)
    : 0x5;
```

### `sourceMap`

Type: `boolean` Default: `false`

为混淆的代码启用源映射生成。

源映射可以帮助您调试混淆的JavaScript源代码。如果希望或需要在生产环境中进行调试，可以将单独的源映射文件上传到一个秘密位置，然后将浏览器指向该位置。

### `sourceMapBaseUrl`

Type: `string` Default: ``

当`sourceMapMode: 'separate'`时，将基本url设置为源映射导入url。

CLI example:

```
javascript-obfuscator input.js --output out.js --source-map true --source-map-base-url 'http://localhost:9000'
```

Result:

```
//# sourceMappingURL=http://localhost:9000/out.js.map
```

### `sourceMapFileName`

Type: `string` Default: ``

当`sourceMapMode: 'separate'`时，设置输出源映射的文件名。

CLI example:

```
javascript-obfuscator input.js --output out.js --source-map true --source-map-base-url 'http://localhost:9000' --source-map-file-name example
```

Result:

```
//# sourceMappingURL=http://localhost:9000/example.js.map
```

### `sourceMapMode`

Type: `string` Default: `separate`

指定源映射生成模式:

- `inline` - 在每个.js文件的末尾添加源映射;
- `separate` - 生成相应的`.map '文件与源映射。如果你通过CLI运行混淆器-添加链接到源映射文件的文件末尾与混淆的代码`//# sourceMappingUrl=file.js.map`。

### `sourceMapSourcesMode`

Type: `string` Default: `sources-content`

允许控制`sources`和`sourcesContent`映射源的字段:

- `sources-content` - 添加虚拟`sources`字段，添加原始源代码的`sourcesContent`字段;
- `sources` - 使用有效的源描述添加`sources`字段，不添加`sourcesContent`字段。当使用NodeJS API时，需要定义`inputFileName`选项，该选项将用作`source`字段值。

### `splitStrings`

Type: `boolean` Default: `false`

将字面值字符串分割为长度为`splitStringsChunkLength`选项值的块。

Example:

```typescript
// input
(function () {
  var test = "abcdefg";
})();

// output
(function () {
  var _0x5a21 = "ab" + "cd" + "ef" + "g";
})();
```

### `splitStringsChunkLength`

Type: `number` Default: `10`

设置`splitStrings`选项的块长度。

### `stringArray`

Type: `boolean` Default: `true`

删除字符串字面量并将其放置在特殊数组中。例如，字符串`"Hello World"`在`var m = "Hello World";`将被替换为类似`var m = _0x12c456[0x1];`

### `stringArrayCallsTransform`

Type: `boolean` Default: `false`

**必须启用`stringArray`选项**

启用对`stringArray`的调用转换。这些调用的所有参数都可以根据`stringArrayCallsTransformThreshold`的值提取到不同的对象。
这使得自动查找字符串数组的调用变得更加困难。

Example:

```
function foo() {
    var k = {
        c: 0x2f2,
        d: '0x396',
        e: '0x397',
        f: '0x39a',
        g: '0x39d',
        h: 0x398,
        l: 0x394,
        m: '0x39b',
        n: '0x39f',
        o: 0x395,
        p: 0x395,
        q: 0x399,
        r: '0x399'
    };
    var c = i(k.d, k.e);
    var d = i(k.f, k.g);
    var e = i(k.h, k.l);
    var f = i(k.m, k.n);
    function i(c, d) {
        return b(c - k.c, d);
    }
    var g = i(k.o, k.p);
    var h = i(k.q, k.r);
}
function j(c, d) {
    var l = { c: 0x14b };
    return b(c - -l.c, d);
}
console[j(-'0xa6', -'0xa6')](foo());
function b(c, d) {
    var e = a();
    b = function (f, g) {
        f = f - 0xa3;
        var h = e[f];
        return h;
    };
    return b(c, d);
}
function a() {
    var m = [
        'string5',
        'string1',
        'log',
        'string3',
        'string6',
        'string2',
        'string4'
    ];
    a = function () {
        return m;
    };
    return a();
}
```

### `stringArrayCallsTransformThreshold`

Type: `number` Default: `0.5`

**必须启用`stringArray`和`stringArrayCallsTransformThreshold`选项**

您可以使用此设置调整对字符串数组的调用将被转换的概率(从0到1)。

### `stringArrayEncoding`

Type: `string[]` Default: `[]`

**必须启用`stringArray`选项**

这个选项会降低脚本的速度。

使用`base64`或`rc4`编码`stringArray`的所有字符串字面量，并插入用于在运行时解码的特殊代码。

每个`stringArray`值都将使用从传递列表中随机选择的编码进行编码。这使得使用多种编码成为可能。

可用的值:

- `'none'` (`boolean`): 不编码`stringArray`的值
- `'base64'` (`string`): 使用`base64`编码`stringArray`值
- `'rc4'` (`string`): 使用`rc4`编码`stringArray`值。**大约比base64慢30-50%**，但更难获得初始值。建议在使用`rc4`编码时禁用`unicodeEscapeSequence`选项，以防止非常大尺寸的混淆代码。

例如，对于以下选项值，一些`stringArray`值将不会被编码，而一些值将使用`base64`和`rc4`编码:

```typescript
stringArrayEncoding: ["none", "base64", "rc4"];
```

### `stringArrayIndexesType`

Type: `string[]` Default: `['hexadecimal-number']`

**必须启用`stringArray`选项**

允许控制字符串数组调用索引的类型。

每个`stringArray`调用索引将由从传递的列表中随机选择的类型进行转换。这使得使用多种类型成为可能。

可用的值:

- `'hexadecimal-number'` (`default`): 将字符串数组调用索引转换为十六进制数
- `'hexadecimal-numeric-string'`: 将字符串数组调用索引转换为十六进制数字字符串

在`2.9.0`发布之前，`javascript-obfuscator`将所有字符串数组调用索引转换为`hexadecimal-numeric-string`类型。这使得一些手动去混淆稍微困难一些，但它允许自动去混淆器轻松检测这些调用。

新的`hexadecimal-number`类型方法使代码中更难自动检测字符串数组调用模式。

未来将添加更多类型。

### `stringArrayIndexShift`

Type: `boolean` Default: `true`

** `stringArray` option must be enabled**

Enables additional index shift for all string array calls

### `stringArrayRotate`

Type: `boolean` Default: `true`

**必须启用`stringArray`选项**

将`stringArray`数组移动到固定和随机的位置(在代码混淆时生成)。这使得将删除的字符串的顺序匹配到原始位置变得更加困难。

### `stringArrayShuffle`

Type: `boolean` Default: `true`

**必须启用`stringArray`选项**

随机打乱`stringArray`数组项。

### `stringArrayWrappersCount`

Type: `number` Default: `1`

**必须启用`stringArray`选项**

为每个根或函数作用域内的`string array`设置包装器的计数。
每个作用域中包装器的实际数量受限于该作用域中文字节点的数量。

Example:

```typescript
// Input
const foo = "foo";
const bar = "bar";

function test() {
  const baz = "baz";
  const bark = "bark";
  const hawk = "hawk";
}

const eagle = "eagle";

// Output, stringArrayWrappersCount: 5
const _0x3f6c = ["bark", "bar", "foo", "eagle", "hawk", "baz"];
const _0x48f96e = _0x2e13;
const _0x4dfed8 = _0x2e13;
const _0x55e970 = _0x2e13;
function _0x2e13(_0x33c4f5, _0x3f6c62) {
  _0x2e13 = function (_0x2e1388, _0x60b1e) {
    _0x2e1388 = _0x2e1388 - 0xe2;
    let _0x53d475 = _0x3f6c[_0x2e1388];
    return _0x53d475;
  };
  return _0x2e13(_0x33c4f5, _0x3f6c62);
}
const foo = _0x48f96e(0xe4);
const bar = _0x4dfed8(0xe3);
function test() {
  const _0x1c262f = _0x2e13;
  const _0x54d7a4 = _0x2e13;
  const _0x5142fe = _0x2e13;
  const _0x1392b0 = _0x1c262f(0xe7);
  const _0x201a58 = _0x1c262f(0xe2);
  const _0xd3a7fb = _0x1c262f(0xe6);
}
const eagle = _0x48f96e(0xe5);
```

### `stringArrayWrappersChainedCalls`

Type: `boolean` Default: `true`

**必须启用`stringArray`和`stringArrayWrappersCount`选项**

启用`string array`包装器之间的链式调用。

Example:

```typescript
// Input
const foo = "foo";
const bar = "bar";

function test() {
  const baz = "baz";
  const bark = "bark";

  function test1() {
    const hawk = "hawk";
    const eagle = "eagle";
  }
}

// Output, stringArrayWrappersCount: 5, stringArrayWrappersChainedCalls: true
const _0x40c2 = ["bar", "bark", "hawk", "eagle", "foo", "baz"];
const _0x31c087 = _0x3280;
const _0x31759a = _0x3280;
function _0x3280(_0x1f52ee, _0x40c2a2) {
  _0x3280 = function (_0x3280a4, _0xf07b02) {
    _0x3280a4 = _0x3280a4 - 0x1c4;
    let _0x57a182 = _0x40c2[_0x3280a4];
    return _0x57a182;
  };
  return _0x3280(_0x1f52ee, _0x40c2a2);
}
const foo = _0x31c087(0x1c8);
const bar = _0x31c087(0x1c4);
function test() {
  const _0x848719 = _0x31759a;
  const _0x2693bf = _0x31c087;
  const _0x2c08e8 = _0x848719(0x1c9);
  const _0x359365 = _0x2693bf(0x1c5);
  function _0x175e90() {
    const _0x310023 = _0x848719;
    const _0x2302ef = _0x2693bf;
    const _0x237437 = _0x310023(0x1c6);
    const _0x56145c = _0x310023(0x1c7);
  }
}
```

### `stringArrayWrappersParametersMaxCount`

Type: `number` Default: `2`

**必须启用`stringArray`选项**

**目前该选项仅影响由`stringArrayWrappersType``function` 选项值添加的包装器**

允许控制字符串数组包装器参数的最大数量。
默认值和最小值为2。建议值为2 ~ 5。

### `stringArrayWrappersType`

Type: `string` Default: `variable`

**必须启用`stringArray`和`stringArrayWrappersCount`选项**

允许选择由`stringArrayWrappersCount`选项附加的包装器类型。

可用的值:

- `'variable'`: 在每个作用域的顶部追加变量包装器。快速的性能。
- `'function'`: 在每个作用域内的随机位置追加函数包装器。性能比变量更慢，但提供了更严格的混淆。

当性能损失对被混淆的应用程序影响不大时，强烈建议使用`function`包装器来实现更严重的混淆。

'function'选项值的示例:

```typescript
// input
const foo = "foo";

function test() {
  const bar = "bar";
  console.log(foo, bar);
}

test();

// output
const a = ["log", "bar", "foo"];
const foo = d(0x567, 0x568);
function b(c, d) {
  b = function (e, f) {
    e = e - 0x185;
    let g = a[e];
    return g;
  };
  return b(c, d);
}
function test() {
  const c = e(0x51c, 0x51b);
  function e(c, g) {
    return b(c - 0x396, g);
  }
  console[f(0x51b, 0x51d)](foo, c);
  function f(c, g) {
    return b(c - 0x396, g);
  }
}
function d(c, g) {
  return b(g - 0x3e1, c);
}
test();
```

### `stringArrayThreshold`

Type: `number` Default: `0.8` Min: `0` Max: `1`

**必须启用`stringArray`选项**

您可以使用此设置来调整将字符串字面值插入到`stringArray`的概率(从0到1)。

此设置对于大代码特别有用，因为它会重复调用字符串数组，并降低代码速度。

`stringArrayThreshold: 0` 等于 `stringArray: false`.

### `target`

Type: `string` Default: `browser`

允许为混淆的代码设置目标环境。

可用的值:

- `browser`;
- `browser-no-eval`;
- `node`.

目前`browser`和`node`目标的输出代码是相同的，但某些浏览器特定的选项不允许与`节点`目标一起使用。
`browser-no-eval`目标的输出代码没有使用`eval`。

### `transformObjectKeys`

Type: `boolean` Default: `false`

启用对象键的转换。

Example:

```typescript
// input
(function () {
  var object = {
    foo: "test1",
    bar: {
      baz: "test2",
    },
  };
})();

// output
var _0x4735 = ["foo", "baz", "bar", "test1", "test2"];
function _0x390c(_0x33d6b6, _0x4735f4) {
  _0x390c = function (_0x390c37, _0x1eed85) {
    _0x390c37 = _0x390c37 - 0x198;
    var _0x2275f8 = _0x4735[_0x390c37];
    return _0x2275f8;
  };
  return _0x390c(_0x33d6b6, _0x4735f4);
}
(function () {
  var _0x17d1b7 = _0x390c;
  var _0xc9b6bb = {};
  _0xc9b6bb[_0x17d1b7(0x199)] = _0x17d1b7(0x19c);
  var _0x3d959a = {};
  _0x3d959a[_0x17d1b7(0x198)] = _0x17d1b7(0x19b);
  _0x3d959a[_0x17d1b7(0x19a)] = _0xc9b6bb;
  var _0x41fd86 = _0x3d959a;
})();
```

### `unicodeEscapeSequence`

Type: `boolean` Default: `false`

允许启用/禁用字符串转换到unicode转义序列。

Unicode转义序列极大地增加了代码大小，并且字符串可以很容易地恢复到原始视图。建议仅对小源代码启用此选项。

## 预设选项

配置`optionsPreset`的选项

### 高混淆，低性能（high-obfuscation）

性能将比没有混淆时慢得多

```javascript
{
    compact: true,
    controlFlowFlattening: true,
    controlFlowFlatteningThreshold: 1,
    deadCodeInjection: true,
    deadCodeInjectionThreshold: 1,
    debugProtection: true,
    debugProtectionInterval: 4000,
    disableConsoleOutput: true,
    identifierNamesGenerator: 'hexadecimal',
    log: false,
    numbersToExpressions: true,
    renameGlobals: false,
    selfDefending: true,
    simplify: true,
    splitStrings: true,
    splitStringsChunkLength: 5,
    stringArray: true,
    stringArrayCallsTransform: true,
    stringArrayEncoding: ['rc4'],
    stringArrayIndexShift: true,
    stringArrayRotate: true,
    stringArrayShuffle: true,
    stringArrayWrappersCount: 5,
    stringArrayWrappersChainedCalls: true,
    stringArrayWrappersParametersMaxCount: 5,
    stringArrayWrappersType: 'function',
    stringArrayThreshold: 1,
    transformObjectKeys: true,
    unicodeEscapeSequence: false
}
```

### 中等混淆，性能最佳（medium-obfuscation）

性能会比没有混淆时慢

```javascript
{
    compact: true,
    controlFlowFlattening: true,
    controlFlowFlatteningThreshold: 0.75,
    deadCodeInjection: true,
    deadCodeInjectionThreshold: 0.4,
    debugProtection: false,
    debugProtectionInterval: 0,
    disableConsoleOutput: true,
    identifierNamesGenerator: 'hexadecimal',
    log: false,
    numbersToExpressions: true,
    renameGlobals: false,
    selfDefending: true,
    simplify: true,
    splitStrings: true,
    splitStringsChunkLength: 10,
    stringArray: true,
    stringArrayCallsTransform: true,
    stringArrayCallsTransformThreshold: 0.75,
    stringArrayEncoding: ['base64'],
    stringArrayIndexShift: true,
    stringArrayRotate: true,
    stringArrayShuffle: true,
    stringArrayWrappersCount: 2,
    stringArrayWrappersChainedCalls: true,
    stringArrayWrappersParametersMaxCount: 4,
    stringArrayWrappersType: 'function',
    stringArrayThreshold: 0.75,
    transformObjectKeys: true,
    unicodeEscapeSequence: false
}
```

### 低混淆，高性能（low-obfuscation）

性能将处于一个相对正常的水平

```javascript
{
    compact: true,
    controlFlowFlattening: false,
    deadCodeInjection: false,
    debugProtection: false,
    debugProtectionInterval: 0,
    disableConsoleOutput: true,
    identifierNamesGenerator: 'hexadecimal',
    log: false,
    numbersToExpressions: false,
    renameGlobals: false,
    selfDefending: true,
    simplify: true,
    splitStrings: false,
    stringArray: true,
    stringArrayCallsTransform: false,
    stringArrayEncoding: [],
    stringArrayIndexShift: true,
    stringArrayRotate: true,
    stringArrayShuffle: true,
    stringArrayWrappersCount: 1,
    stringArrayWrappersChainedCalls: true,
    stringArrayWrappersParametersMaxCount: 2,
    stringArrayWrappersType: 'variable',
    stringArrayThreshold: 0.75,
    unicodeEscapeSequence: false
}
```

### 默认设置，高性能（default）

```javascript
{
    compact: true,
    controlFlowFlattening: false,
    deadCodeInjection: false,
    debugProtection: false,
    debugProtectionInterval: 0,
    disableConsoleOutput: false,
    identifierNamesGenerator: 'hexadecimal',
    log: false,
    numbersToExpressions: false,
    renameGlobals: false,
    selfDefending: false,
    simplify: true,
    splitStrings: false,
    stringArray: true,
    stringArrayCallsTransform: false,
    stringArrayCallsTransformThreshold: 0.5,
    stringArrayEncoding: [],
    stringArrayIndexShift: true,
    stringArrayRotate: true,
    stringArrayShuffle: true,
    stringArrayWrappersCount: 1,
    stringArrayWrappersChainedCalls: true,
    stringArrayWrappersParametersMaxCount: 2,
    stringArrayWrappersType: 'variable',
    stringArrayThreshold: 0.75,
    unicodeEscapeSequence: false
}
```
