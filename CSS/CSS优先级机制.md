# CSS优先级机制

### 样式优先级
外部样式、内部样式和内联样式同时应用于同一个元素，就是使多重样式的情况
一般情况下
```text
（外部样式）External style sheet <（内部样式）Internal style sheet <（内联样式）Inline style
```
注意，有一个例外的情况，当外部样式放在内部样式的后面，则外部样式将覆盖内部样式
```html
<html>
<head>
    <style type="text/css">
      /* 内部样式 */
      h1{ color:red; }
    </style>
    <!-- 外部样式 style.css -->
    <link rel="stylesheet" type="text/css" href="style.css"/>
    <!--
      style.css内容：
      h1 { color: green; }
    -->
</head>
<body>
    <h1>标题</h1>
</body>
</html>
```

### CSS优先级法则
#### 不同级别
1. !important的样式会覆盖页面内任何位置定义的样式
2. 作为style属性写在元素内的样式
3. ID选择器
4. 类选择器
5. 元素选择器
6. 通配符选择器
7. 继承
8. 浏览器默认属性

总结： `!important > 行内样式 > ID选择器 > 类选择器 > 元素选择器 > 通配符选择器 > 继承 > 浏览器默认属性`

#### 同一级别
同一级别中后写的会覆盖先写的样式

优先级相同时，则采用就近原则，选择最后出现的样式

### 高效CSS书写
1. 不要在ID选择器前使用元素名
2. 如果没有相同的名字出现，不要在类选择器前使用元素名
3. 尽量少使用层级关系， 使用类选择器代替层级关系
