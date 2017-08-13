# CSS3动画初识
CSS 动画由两个基本块构成
1. Keyframes - 关键帧
2. Animation Properties - 动画属性

### 关键帧(Keyframes)
关键帧是CSS动画的基础，在每个阶段的动画时间轴定义动画的样子

每个`@keyframes`由以下部分组成
1. `动画的名称`：描述动画的名称，如`bounceIn`
2. `动画的阶段`：动画的每个阶段都用百分比表示，`0%`代表了动画的开始状态，`100%`代表了动画的结束状态，此外还可以添加多个中间状态
3. `动画的属性`：在每个动画阶段定义的css属性

一个简单的`@keyframes`例子，这个`@keyframes`有三个阶段，在第一阶段(`0%`)，元素为完全透明和10%的缩放大小，在第二阶段(`60%`)，元素消失完全不透明和120%的缩放大小，在最后阶段(`100%`), 元素返回默认大小
```css
@keyframes bounceIn {
  0% {
    transform: scale(0.1);
    opacity: 0;
  }
  60% {
    transform: scale(1.2);
    opacity: 1;
  }
  100% {
    transform: scale(1);
  }
}
```

### 动画属性
动画属性用来做两件事
- 分配`@keyframes`到需要发生动画的元素中
- 定义如何动画（有点拗口，但就是这么个意思。。。）

添加动画属性到CSS选择器(或元素), 必须添加以下两个动画属性来使动画生效:
- `animation-name`：动画的名称，由`@keyframes`定义
- `animation-duration`：动画的持续时间, 以秒为单位(如：5s)或毫秒(如：200ms)。

举个栗子🌰：

使一个div发生上面定义的`bounceIn`动画：
```css
div {
  animation-duration: 2s;
  animation-name: bounceIn;
}
```
也可以用`animation`属性简写：
```css
div {
  animation: bounceIn 2s;
}
```
### 动画属性简写
每个动画属性都可以单独定义，但是为了使代码更清晰简洁，建议使用简写方式：

```txt
animation: [animation-name] [animation-duration] [animation-timing-function] [animation-delay] [animation-iteration-count] [animation-direction] [animation-fill-mode] [animation-play-state];
```
需要注意参数顺序，并且前两个参数为必须的

实栗🌰：
![bounceIn](assets/bouncein.gif)

### 浏览器前缀

许多基于Webkit的浏览器仍然使用-webkit-prefixed版本的动画,关键帧和转换

```css
div {
  -webkit-animation-duration: 2s;
  animation-duration: 2s;
  -webkit-animation-name: bounceIn;
  animation-name: bounceIn;
}
```
```css
@-webkit-keyframes bounceIn { /* styles */ }
@keyframes bounceIn { /* styles */ }
```
在他们采用标准版之前, 需要将-webkit前缀加入

### 其他动画属性

除了必需的`animation-name`和`animation-duration`动画属性, 还可以进一步自定义和创建复杂的动画:

- `animation-timing-function`
- `animation-delay`
- `animation-iteration-count`
- `animation-direction`
- `animation-fill-mode`
- `animation-play-state`

#### Animation-timing-function

`animation-timing-function` 定义了动画的速度曲线, 默认值：`ease`

```txt
animation-timing-function: value;
```
预设值：
- `linear`: 动画从头到尾的速度是相同的
- `ease`: 默认。动画以低速开始，然后加快，在结束前变慢
- `ease-in`: 动画以低速开始
- `ease-out`: 动画以低速结束
- `ease-in-out`: 动画以低速开始和结束
- `cubic-bezier(n,n,n,n)`: 在 cubic-bezier 函数中自定义值。n可能是从 0 到 1 的数值

#### Animation-Delay
