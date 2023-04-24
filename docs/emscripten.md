## wasm 运行原理

webassembly 标准提供将 wasm 解析成 webassembly 模块的方式。然后提供一个对此模块进行访问的 js 实例，这个实例对象可以操作和访问模块中的数据和函数。

```javascript
// 加载 WebAssembly 模块
WebAssembly.instantiateStreaming(fetch("my_module.wasm")).then(function (obj) {
  // 实例化 WebAssembly 模块
  var instance = obj.instance;

  // 调用 WebAssembly 模块中的函数
  var result = instance.exports.my_function(42);

  console.log("Result: " + result);
});
```

## 导出

Emscripten 最后会导出一个全局对象 Module。

## 异步加载

加载 wasm 的过程是异步的，onRuntimeInitialized 后才说明 Module 加载完成。

## js 调用 c++导出函数

通过将函数导出
