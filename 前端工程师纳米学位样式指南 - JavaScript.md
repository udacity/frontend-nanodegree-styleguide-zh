---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: true

print_background: false
---

# 前端工程师纳米学位样式指南 - JavaScript

点此查看文档英文版（[pdf](https://s3.cn-north-1.amazonaws.com.cn/static-documents/nd001/Udacity+Nanodegree+Style+Guide_JavaScript_EN.pdf)，[GitHub.io](http://udacity.github.io/frontend-nanodegree-styleguide/javascript.html)）

## 零. 简介

该指南是你在项目进行过程中所需遵守的官方指南。优达学城的评估人员会根据该指南为你的项目打分。在前端网页开发的世界中，有很"最佳"样式供你选择。因此，为了减少学生在项目过程中因选择何种样式所产生的困惑，我们强烈建议所有学生在其项目中遵循这个样式指南。

## 一. 通用规则

### 1.1 编码

使用 UTF-8（无 BOM）。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。

### 1.2 末尾空白

删除行尾空格。

行尾空格属于多余的符号，并且会让 diff 变得更加复杂。

**不推荐：**

```javascript
const name = "John Smith";__
```

**推荐：**

```javascript
const name = "John Smith";
```

如果你使用 VS Code，你可进入编辑器菜单的「首选项——>设置」中搜索 `files.trimTrailingWhitespace` ，然后将选项勾选即可，这样每当你保存文件时，去除行尾空格操作便会自动完成：

```json
"files.trimTrailingWhitespace": true
```

### 1.3 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

### 1.4 注释

用注释解释代码的覆盖范围、目的和作用以及使用和选择各解决方案的原因。

你可以选择使用 [JSDoc](http://usejsdoc.org/)，即编写代码注释的文件生成器和标准，对你的 JavaScript 功能进行记录，其优点包括为你的注释提供技术参照和能够针对文件生成网页的命令行 jsdoc 工具。 JSDoc 会为你提供记录代码的多种注释，但我们只推荐你使用以下种类：

- [@constructor](http://usejsdoc.org/tags-class.html)：用于记录一个 Class 类，也就是用 `new` 关键字调用的函数。
- [@description](http://usejsdoc.org/tags-description.html)：用于描述你的函数，该标签还可以使你在需要时添加 HTML 标记。
- [@param](http://usejsdoc.org/tags-param.html)：用于描述函数参数的名称、类别和说明。
- [@returns](http://usejsdoc.org/tags-returns.html)：记录函数返回值的类型和说明。

下方实例说明了如何记录类构造函数（注意注释区开头使用的 `/**` ，这个非常重要）：

```javascript
/**
* @description 简要描述这本书
* @constructor
* @param {string} title - 书的标题
* @param {string} author - 书的作者
*/

function Book(title, author) {
   ...
}
```

以下函数含有能返回值的参数，注意，这里的参数作用一目了然，因此并未对其进行说明。

```javascript
/**
* @description 计算两数相加
* @param {number} a
* @param {number} b
* @returns {number} 数字 a 与 b 的和
*/

function sum(a, b) {
   return a + b;
}
```

你也可以使用更多你想要编写的注释。

### 1.5 待办任务

用 `TODO:` 标注待办事项和任务项

仅用关键词 `TODO` 标注待办事项，不要使用 `@@` 等其他格式的字样。在任务项前加冒号，如： `TODO: 待办任务`

**推荐：**

```javascript
// TODO: 加些其他的需求
```

## 二. JavaScript 语言规则

### 2.1 变量

在 JavaScript 里一共有三种定义变量的方式：

- [const](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const)
- [let](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let)
- [var](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/var)

当定义变量的时候，你应该使用上面列出的关键字来定义变量。优先考虑使用 `const` 定义你的变量，如果觉得以后需要对变量重新赋值的，则使用 `let`。现在已经不推荐使用 `var` 关键字来定义变量了。

### 2.2 分号

始终使用分号。

依靠隐式插入会造成难以排除的细微问题。分号应放在**函数表达式**的末尾，而不是**函数声明**的末尾。

**不推荐：**

```javascript
const foo = function() {
   return true // 缺少分号
} // 缺少分号
function foo() {
   return true;
}; // 额外的分号
```

**推荐：**

```javascript
const foo = function() {
   return true;
};
function foo() {
   return true;
}
```

### 2.3 基本类型包装对象

基本类型无需使用包装对象，此外，包装对象还具有潜在危险，但可以使用类型转换。

**不推荐：**

```javascript
const x = new Boolean(0);
if (x) {
   alert('hi');	// 如果 x 是一个真实对象，则显示 hi
}
```

**推荐：**

```javascript
const x = Boolean(false);
if (x) {
   alert('hi');	// 如果 x 是一个否定的布尔值，则显示 hi
}
```

### 2.4 闭包

进行该操作时要小心谨慎。 创建闭包的能力可能是 JavaScript 中最有用但最常被忽略的能力。需要记住的是，闭包会储存对其封闭范围的指针，因此，将 DOM 元素与闭包相连会生成循环引用，从而导致内存的泄露。

**不推荐：**

```javascript
function foo(element, a, b) {
   element.onclick = function() { /* 使用 a 和 b */ }
}
```

**推荐：**

```javascript
function foo(element, a, b) {
   element.onclick = bar(a, b);
}
function bar(a, b) {
   return function() { /* 使用 a 和 b */ }
}
```

### 2.5 for 、for-in 和 forEach

### 2.6 数组

在迭代数组时，相比 `for-in` 循环， `forEach` 或 `for` 循环更具优势。

**不推荐：**

```javascript
const myArray = ['a', 1, 'etc'];
for (const indexNum in myArray) {
   console.log(myArray[indexNum]);
}
const starWars = {
   "creatures": [
      {
         "name": "bantha",
         "face": "furry"
      },
      {
         "name": "loth-cat",
         "face": "toothy"
      }
   ]
};
for (const i in starWars.creatures) {
   console.log(starWars.creatures[i].name);
   console.log(starWars.creatures[i].face);
};
```

**推荐：**

```javascript
const mySimpleArray = ['a', 1, 'etc'];
const mySimpleArray.forEach(function(val) {
   console.log(val);
});
const starWars = {
   "creatures": [
      {
         "name": "bantha",
         "face": "furry"
      },
      {
         "name": "loth-cat",
         "face": "toothy"
      }
   ]
};
starWars.creatures.forEach(function(creature){
   console.log(creature.name);
   console.log(creature.face)
});
// 或者
const myArray = ['a', 1, 'etc'];
for (let indexCount = 0; indexCount < myArray.length; indexCount++) {
   console.log(myArray[indexCount]);
};
```

### 2.6 对象

`for-in` 循环用于在对象中循环关键词。这样很容易出错，因为， `for-in` 不会从 `0` 循环，而是循环对象及其原型链中现存的所有关键词。 如果可以的话，对数据进行整理，以避免迭代对象。如果不可行，将 `for-in` 循环的内容包裹在条件语句中，以避免迭代原型链。

`for-in` 循环用于循环对象中的键。这很容易出错，因为 `for-in` 不是从 `0` 循环到 `length-1` ，而是循环对象及其**原型链**中的所有现有键。

如果可以的话，对数据进行整理，这样就不必在对象上迭代。如果不可行，就将 `for-in` 循环的内容包裹在条件语句中，以防止它在原型链上迭代。

**不推荐：**

```javascript
const myObj = {'firstName':'Ada','secondName':'Lovelace'};
for (const key in myObj) {
   console.log(myObj[key]);
}
```

**推荐：**

```javascript
const myObj = {'firstName':'Ada','lastName':'Lovelace'};
for (const key in myObj) {
   if (myObj.hasOwnProperty(key)) {
      console.log(myObj[key]);
   }
}
```

### 2.7 多行字符串字面量

不要使用。 编译期间无法妥善删除各行开头的空格，斜杠后的空白会引发棘手的问题，虽然大部分脚本引擎支持该操作，但这并不属于规格中的一部分。

**不推荐：**

```javascript
const myPoetry = '一二三四五，\
   上山打老虎，\
   老虎没打到，\
   打到小松鼠，\
   让我数一数，\
   一二三四五';
```

**推荐：**

```javascript
const myPoetry = '黄河远上白云间，' +
   '一片孤城万仞山。' +
   '羌笛何须怨杨柳，' +
   '春风不度玉门关。';

// or
const myPoetry = `
   黄河远上白云间，
   一片孤城万仞山。
   羌笛何须怨杨柳，
   春风不度玉门关。
`;
```

### 2.8 数组和对象字面量

使用数组和对象字面量，而不是数组和对象构造函数。

**不推荐：**

```javascript
const myArray = new Array(x1, x2, x3);
const myObject = new Object();
myObject.a = 0;
```

**推荐：**

```javascript
const myArray = [x1, x2, x3];
const myObject = {
   a: 0
};
```

## 三. JavaScript 样式规则

### 3.1 命名

总体来说，函数名称为 `functionNames` ，变量名称为 `variableNames` ，类名称为 `ClassNames` ，方法名称为 `methodNames` ，常量值名称为 `CONSTANT_VALUES` ，文件名称为 `filenames` 。

### 3.2 代码格式

由于分号的隐式插入，大括号应与其内容放置在同一行。

**推荐：**

```javascript
if (something) {
   // 执行某项任务
} else {
   // 执行另外一项任务
}
```

只有在单行数组和对象初始器可以在写同一行时方可使用这两项。左括号前和右括号后都不应有空格。

**推荐：**

```javascript
const array = [1, 2, 3];
const object = {a: 1, b: 2, c: 3};
```

多行数组和对象初始器需进行单行缩进，与代码块一样，其括号与内容应位于同一行。

**推荐：**

```javascript
const array = [
   'Joe <joe@email.com>',
   'Sal <sal@email.com>',
   'Murr <murr@email.com>',
   'Q <q@email.com>'
];

const object = {
   id: 'foo',
   class: 'foo-important',
   name: 'notification'
};
```

### 3.3 字符串

为了保持连贯性，应使用单引号 `'` 而不是双引号 `"`。这在创建含有 HTML 的字符串时尤其有帮助。

**推荐：**

```javascript
const element = 'Click Me';
```

此规则较为明显的一个例外是在 JSON 对象中： **JSON 要求使用双引号**。

## 四. 技巧提示

### 4.1 真假布尔表达式

以下为**假**的布尔表达式：

- `null`
- `undefined`
- `''` 空字符串
- 数字 `0`

注意区分，以下为**真**的表达式：

- `'0'` 字符串0
- `[]` 空数组
- `{}` 空对象

### 4.2 三元表达式 `expr ? A : B`

不强制规定，但建议使用三元条件运算符编写简洁代码，避免使用以下代码：

**不推荐：**

```javascript
if (val) {
   return foo();
} else {
   return bar();
}
```

**推荐：**

```javascript
return val ? foo() : bar();
```

### 4.3 短路求值 `&&` 和 `||`

短路求值是一种逻辑运算符的求值策略。只有当第一个运算数的值无法确定逻辑运算的结果时，才对第二个运算数进行求值。例如，当 `&&` 的第一个运算数的值为 `false` 时，其结果必定为 `false` ；当 `||` 的第一个运算数为 `true` 时，最后结果必定为 `true` ，在这种情况下，就不需要知道第二个运算数的具体值。

**不推荐：**

```javascript
function foo(name) {
   let theName;
   if (name) {
      theName = name;
   } else {
      theName = 'John';
   }
   return theName;
}
```

**推荐：**

```javascript
function foo(name) {
   return theName = name || 'John';
}
```

#### 4.4 && 也被用于缩减代码

**不推荐：**

```javascript
if (node) {
   if (node.kids) {
      console.log(node.kids);
   }
}
```

**推荐：**

```javascript
if (node && node.kids) {
   console.log(node.kids);
}
```
