
### 2.1.2 CommonJS 的模块规范

CommonJS 主要分为模块引用、模块定义和模块标识3个部分。

#### 1. 模块引用

模块引用的示例代码如下：

```javascript
var math = require('math');
```

在 CommonJS 规范中，存在`require()`方法，这个方法引入模块标识，以此引入一个模块的 API 到当前上下文中。

#### 2. 模块定义

上下文提供了`exports`对象用于导出当前模块的方法或变量，并且它是惟一的出口。

在模块中，存在`module`对象，它代表模块自身，而`exports`是`module`的属性。

在 Node.js 中，一个文件就是一个模块，将方法挂载到`exports`对象上作为属性即可定义导出的方式：

```javascript
// math.js
exports.add = function () {
    // ...
}
```

在另一个模块中，通过`require()`引入模块后，就能调用定义的属性或方法了：

```javascript
// program.js
var math = require('math');

exports.increment = function (val) {
    return math.add(val, 1);
}
```

#### 3 模块标识

模块标识其实就是传递给`require()`方法的参数，它必须是满足小驼峰命名的字符串，或者以`.`、`..`开头的相对路径，或者绝对路径。它可以没有文件名后缀`.js`。
