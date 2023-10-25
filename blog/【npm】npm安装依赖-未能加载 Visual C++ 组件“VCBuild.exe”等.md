windows系统打开
控制面板 —> 系统和功能 —> 启用或关闭windows功能
把这一项勾中.NET Framework 3.5（包括.NET2.0和3.0）。
再次安装依赖报错：
```javascript
MSBUILD : error MSB3428: 未能加载 Visual C++ 组件“VCBuild.exe”。要解决此问题，1) 安装 .NET Framework 2.0 SDK；2) 安装 Microsoft Visual Studio 2005；或 3) 如果将该组件安装到了其他位置，请将其位置添加到系统路径中。 [D:\manage\web\node_modules\utf-8-validate\bui
ld\binding.sln]
```
解决方法：
在命令行工具中运行以下命令 （全局安装windows构建工具）
```javascript
npm install –global –production windows-build-tools
```
