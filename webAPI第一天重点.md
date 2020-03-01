## DOM

概念：W3C 组织规定的处理可扩展标记语言（HTML/XML）的一套规范

## 获取元素

- 通过 ID 获取一个

```javascript
// 前面一定要跟 document
var oUl = document.getElementById('ul1');
console.log(oUl, typeof oUl); // 'object'
```

- 通过标签名获取一组

```html
<ol id="ol1">
    <li>ol1</li>
    <li>ol2</li>
    <li>ol3</li>
</ol>
```

```javascript
var oOl = document.getElementById('ol1');
// 注意返回的是一个伪数组
var aLi = oOl.getElementsByTagName('li');
console.dir(aLi);
```

```javascript
var aOl = document.getElementsByTagName('ol'); // [ol]
// 注意 getElementsByTagName 签名一定是单个元素！！！
var aLi = aOl[0].getElementsByTagName('li');
console.dir(aLi);
```

- 通过 class 获取一组

```javascript
// 一定要注意返回的是一个伪数组
var aOl = document.getElementsByClassName('ol1');
console.log(aOl);
```

- 通过 query 系列

```javascript
// 获取单个，querySelector 只能获取到符合条件的第一个
// 获取 ol 里面的第一个 li 元素
var oLi = document.querySelector('ol li');
// var oLi = document.querySelector('ol li:first-child');
console.log(oLi);
```

```javascript
// 获取一组
// 获取 ol 里面的所有的 li
var aLi = document.querySelectorAll('ol li');
console.log(aLi);
```

- 两个特殊

```javascript
document.body // 获取 body
document.documentElement // 获取 html
```

## 事件

- 事件三要素

```javascript
// 事件源，事件类型，事件处理程序
// 开关（事件源）被按下（事件类型）灯亮了（事件处理程序）
oBtn.onclick = function() {
    console.log('大家辛苦啦~~');
};
```

## 改变普通元素内容

- innerText，设置的时候不会解析 HTML 标签，获取的时候只识别文本

```javascript
var oDiv = document.querySelector('#box1');
// oDiv.innerText = '<strong>hello</strong> world';
oDiv.innerHTML = '<strong>hello</strong> world';
```

- innerHTML，设置的时候会解析 HTML 标签，获取的时候都识别（文本、空格、换行、标签）

## 常见元素的属性的修改

```javascript
// 都是通过点（.）进行
oImg.src = 'test.png';
oImg.title = 'hello';
```

```javascript
// 表单元素的属性操作
oInput.value = '修改表单元素的内容用的是value，不要用innerText或innerHTML';
```

## 样式属性操作

- 通过 style 修改行内样式

```javascript
var oDiv = document.querySelector('div');
// 通过 JS 加一些基础的样式
oDiv.style.width = '100px';
oDiv.style.height = '100px';
oDiv.style.backgroundColor = 'red';
oDiv.style.transition = '.6s';

oDiv.onclick = function() {
    // oDiv.style.transform = 'rotate(330deg)';
    this.style.transform = 'rotate(330deg)';
};
```

- 通过 className 修改元素的 class（非行内）