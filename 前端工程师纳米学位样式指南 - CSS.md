# 前端工程师纳米学位样式指南 - CSS

点此查看文档英文版（[pdf](https://s3.cn-north-1.amazonaws.com.cn/static-documents/nd001/Udacity+Nanodegree+Style+Guide_JavaScript_EN.pdf)，[GitHub.io](http://udacity.github.io/frontend-nanodegree-styleguide/javascript.html)）

## 简介

该指南是你在项目进行过程中所需遵守的官方指南。优达学城的评估人员会根据该指南为你的项目打分。在前端网页开发的世界中，有很"最佳"样式供你选择。因此，为了减少学生在项目过程中因选择何种样式所产生的困惑，我们强烈建议所有学生在其项目中遵循这个样式指南。

## 一般格式规则

### 字母大小写

仅使用小写。

所有代码均使用小写，该规则适用于 CSS 选择符、属性和属性值（字符串除外）。

**不推荐：**

`color: #E5E5E5;`

**推荐：**

`color: #e5e5e5;`

### 末尾空格

删除行尾空格。

行尾空格属于多余的符号，会使 diff 更加难以阅读。

**不推荐：**

`border: 0;__`

**推荐：**

`border: 0;`

如果使用 Sublime Text，你可在用户设置（User Settings）JSON 文件（可在文本编辑器的菜单中找到）中添加以下代码，每当你以此方法储存文件时，去除行尾空格操作便会自动完成：

`"trim_trailing_white_space_on_save": true`

### 缩进

整个文件中的缩进应保持前后一致，使用 Tab、2个空格或4个空格都可以，但需保持前后一致。

## 一般元规则

### 编码

使用 UTF-8（无 BOM）。

确保你的编辑器将没有字节顺序标记的 UTF-8 用作字符编码。不要将样式表的编码设置为假定的 UTF-8。

### 注释

在可行和必要时，对代码添加注释。

用注释解释代码的覆盖范围、目的和作用以及使用和选择各解决方案的原因。

### 任务项

用 TODO: 标注待办事项和任务项：

仅用关键词 TODO 标注待办事项，不要使用 @@ 等其他格式的字样。在任务项前加冒号，如：TODO: action item。

**推荐：**

`/* TODO: 添加一个按钮元素 */`

## CSS 样式规则

### CSS 有效性

使用有效的 CSS。

使用有效的 CSS 是可测量的基准质量，可确保 CSS 的合理使用并有助于识别可删除的无效 CSS 代码。

### ID 和类名称

使用有意义或具有普遍性的 ID 和类名称。

不可使用意义含糊的 ID 和类名称，使用能够反映相应元素意义的名称或具有普遍性的通用名。

最好使用能够反映相应元素意义的具体名称，因为这些名称最易于理解且不易变更。

具有普遍性的通用名被用于与类似元素意义相仿的元素，主要起辅助作用。

**不推荐：**

```css
.p-998 { 
	… 
} 

.btn-green { 
	… 
}

```

推荐：

```css
.gallery { 
	…
} 

.btn-default { 
	… 
}

```

### 类型选择符

避免用类型选择器限定 ID 和类名称。

除非情况需要（例如，在辅助类型中），否则不要将元素名和 ID 或类名称同时使用。为提高性能，避免使用不必要的祖先选择符。

在 CSS 文件中使用 ID 也是较糟糕的做法，类别始终比名称更具优势，如果你需要给予某元素一个特殊的名称，请使用类别。（ ID 的唯一优点是在存在数千个类似元素的页面上能保持较快的运行速度。）

**不推荐：**

```css
ul#example { 
	… 
} 

div.error { 
	… 
}

```

**推荐：**

```css
.example { 
	… 
} 

.error { 
	… 
}

```

### 简写属性

应使用简写。

CSS 可提供多种简写属性（例如，padding，而不是 padding-top、padding-bottom 等），应尽可能使用这些简写，但字体属性和在 Bootstrap 等框架中会覆盖其他同名属性的属性除外。

使用简写属性有助于提高代码的效率和易懂性。推荐在设置仅与字体 font 相关的属性时使用字体简写属性，但无需在进行小幅改动时使用。在使用字体简写属性时，请注意，如果未注明字体的大小和系列，浏览器会忽略整个字体声明。

不推荐：

```css
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%; 
line-height: 1.6; 
padding-bottom: 2em; 
padding-left: 1em; 
padding-right: 1em; 
padding-top: 0;
```

**推荐：**

```css
border-top: 0; 
font: 100%/1.6 palatino, georgia, serif; 
padding: 0 1em 2em;

```

### 0和单位

去掉 `0` 值后面的单位。

**不推荐：**

```css
margin: 0em; 
padding: 0px;

```

**推荐：**

```css
margin: 0; 
padding: 0;

```

### 前导零

为方便阅读，十进制值中含有前导零。

**不推荐：**

`font-size: .8em;`

**推荐：**

`font-size: 0.8em;`

### 十六进制表示法

在可行时，使用三个十六进制表示法的字符。

**不推荐：**

`color: #eebbcc;`

**推荐：**

`color: #ebc;`

### ID 和类名称分隔符

用连字符分隔 ID 和类名称中的字词（-）。

用连字符连接选择符中的词语和缩略词，以方便理解和扫描。

唯一的例外：在编写 BEM 样式 CSS 选择符时也可以使用下划线（_）。

**不推荐：**

```css
.demoimage { 
	… 
} 

.errorStatus {
	 …
}

```

**推荐：**

```css
.demo-image { 
	… 
} 

.error-status { 
	… 
}

```

### Hack

避免用户代理检测或 CSS Hack ——尝试另一种方法。

人们可能很想处理用户代理检测或特殊的 CSS 过滤器以及应变方案和非法入侵之间的样式差异。这两项措施均为实现和维护有效和可处理的代码库的最后方案。请考虑该样式是否对应用的性能至关重要，需要该样式的用户代理是否可以不采样该样式。

## CSS 格式规则

### 代码块内容缩进

缩进所有代码块内容，即规则内的规则和声明，以反映层次结构、方便理解。

推荐：

```css
@media screen, projection { 
	html { 
		background: #fff; 
		color: #444; 
	} 
}

```

### 声明标点

在所有声明后使用分号，以增加连贯性和延展性。

**不推荐：**

```css
.test { 
	display: block; 
	height: 100px 
}

```

**推荐：**

```css
.test { 
	display: block;
	height: 100px; 
}

```

### 属性名标点

所有属性名冒号后均需添加空格，但属性和冒号间不加空格，以增加连贯性。

**不推荐：**

```css
font-weight:bold;
padding : 0;
margin :0;

```

**推荐：**

```css
font-weight: bold;
padding: 0; 
margin: 0;

```

### 声明区标点

最后一个选择符和声明区起始处的左大括号之间需加空格。

**不推荐：**

```css
.video-block{ 
	margin: 0; 
} 

.audio-block{ 
	margin: 0;
}

```

**推荐：**

```css
.video-block { 
	margin: 0; 
} 

.audio-block { 
	margin: 0; 
}

```

### 选择符和声明分隔

所有选择符和声明均需另起一行。

**不推荐：**

```css
h1, h2, h3 { 
	font-weight: normal; 
	line-height: 1.2; 
}

```

**推荐：**

```css
h1, 
h2, 
h3 { 
	font-weight: normal; 
	line-height: 1.2; 
}

```

### 规则分隔

所有规则间均需加一个空行（两个换行符）。

**推荐：**

```css
html { 
	background: #fff; 
} 

body { 
	margin: auto; 
	width: 50%; 
}

```

### CSS 引号

属性选择符和属性值均需使用双引号，链接值（ url()）中不可使用双引号。

**不推荐：**

```css
@import url("css/links.css"); 
html { 
	font-family: 'Open Sans', arial, sans-serif; 
}

```

**推荐：**

```css
@import url(css/links.css); 
html { 
	font-family: "Open Sans", arial, sans-serif; 
}

```

## CSS 元规则

### 区块注释

在可行时，用注释将样式表区块组合在一起，用新行分隔各区块。

**推荐：**

```css
/* Header */
.header {
…
}

.header-nav {
…
}

/* Content */
.gallery {
…
}

.gallery-img {
…
}

/* Footer */
.footer {
…
}

.footer-nav {
…
}
```
