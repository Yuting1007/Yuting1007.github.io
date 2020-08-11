---
layout: post
title: "Greating from Iris"
date: 2020-08-10
tag: Interview
---
[Reference](https://github.com/yangshun/front-end-interview-handbook/blob/master/contents/en/css-questions.md)
[一套操作题](https://juejin.im/post/6844903816672837639#heading-8)

#### float && clear [ref](https://css-tricks.com/all-about-floats/)
Float is a CSS positioning property. Floated elements remain a part of the flow of the page, and will affect the positioning of other elements (e.g. text will flow around floated elements), unlike `position: absolute` elements, which are removed from the flow of the page.
(things might undereath it, but not texting element)

An element that has the `clear`property set on it will not move up adjacent to the float like the float desires, but will move itself down past the float.

#### z-index
The `z-index` property in CSS controls the vertical stacking order of elements that overlap. `z-index` only affects elements that have a `position` value which is not `static`.

A stacking context is an element that contains a set of layers.
If an element B sits on top of element A, a child element of element A, element C, can never be higher than element B even if element C has a higher `z-index` than element B.

####  Describe Block Formatting Context (BFC) and how it works.
A [Block Formatting Context](http://www.w3.org/TR/CSS21/visuren.html#block-formatting) is part of the visual CSS rendering of a web page in which block boxes are laid out.

A BFC is an HTML box that satisfies at least one of the following conditions:

-   The value of  `float`  is not  `none`.
-   The value of  `position`  is neither  `static`  nor  `relative`.
-   The value of  `display`  is  `table-cell`,  `table-caption`,  `inline-block`,  `flex`, or  `inline-flex`.
-   The value of  `overflow`  is not  `visible`.
(The `overflow` property specifies what should happen if content overflows an element's box.)
In a BFC, each box's left outer edge touches the left edge of the containing block (for right-to-left formatting, right edges touch).

Vertical margins between adjacent block-level boxes in a BFC collapse. Read more on  [collapsing margins](https://www.sitepoint.com/web-foundations/collapsing-margins/).

#### boxing model, box sizing
The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. Each box has a `content` area (e.g. text, an image, etc.) and optional surrounding `padding`, `border`, and `margin` areas.

-   The dimensions of a block element are calculated by  `width`,  `height`,  `padding`,  `border`s, and  `margin`s.
-   If no  `height`  is specified, a block element will be as high as the content it contains, plus  `padding`  (unless there are floats, for which see below).
-   If no  `width`  is specified, a non-floated block element will expand to fit the width of its parent minus  `padding`.
-   The  `height`  of an element is calculated by the content's  `height`.
-   The  `width`  of an element is calculated by the content's  `width`.
-   By default,  `padding`s and  `border`s are not part of the  `width`  and  `height`  of an element.

__important__, by default, the padding and border are not part of the box element `*{ box-sizing : content-box}`. 
But, if we using `* { box-sizing: border-box}`, the padding and boarder are in the calculation. 

#### horizontal centering, flexbox layout
[Ref](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- flex-container
`flex-direction`, `flex warp`, `flex-flow`, `justify-content` (main axis), `align-items` (cross axis)

- flex-items
`order`, `flex-grow`, `flex-shrink`

- centering in CSS
[Ref](https://css-tricks.com/centering-css-complete-guide/)

	__Horizontally__
	If we are in a inline-level parent level, we can just use, `text-align: center`; if we are in a block level element, we can center it by giving it margin-left and margin-right of `auto`, if we have multiple block elements that need to be centerm we can change their display type and use flex-box layout
	__Vertically__
a bit tricky.

But, if we can use flex
horizontally
```
.parent  {  display: flex;  flex-direction: row;  justify-content: center;  }
```
veritically
```
.flex-center-vertically  {  display: flex;  justify-content: center;  flex-direction: column;  height:  400px;  }
```
both
```
.parent  {  display: flex;  justify-content: center;  align-items: center;  }
```
```
[theme.breakpoints.down('sm')]: {
width:  '40%',
}
```
	
#### display
- `none`, `block`, `inline`, `inline-block`, `flex`, `grid`, `table`, `table-row`, `table-cell`, `list-item`.

| `display` | Description |
| :-- | :-- |
| `none` | Does not display an element (the elementv no longer affects the layout of the document). All child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree |
| `block` | The element consumes the whole line in the block direction (which is usually horizontal) |
| `inline` | Elements can be laid out beside each other |
| `inline-block` | Similar to `inline`, but allows some `block` properties like setting `width` and `height` |
| `table` | Behaves like the `<table>` element |
| `table-row` | Behaves like the `<tr>` element |
| `table-cell` | Behaves like the `<td>` element |
| `list-item` | Behaves like a `<li>` element which allows it to define `list-style-type` and `list-style-position` |

#### What's the difference between a  `relative`,  `fixed`,  `absolute`  and  `static` positioned element?
[Document](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
A positioned element is an element whose computed  `position`  property is either  `relative`,  `absolute`,  `fixed`  or  `sticky`.

-   `static`  - The default position; the element will flow into the page as it normally would. The  `top`,  `right`,  `bottom`,  `left`  and  `z-index`  properties do not apply.
-   `relative`  - The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
-   `absolute`  - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
-   `fixed`  - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.
-   `sticky`  - Sticky positioning is a hybrid of relative and fixed positioning. The element is treated as  `relative`  positioned until it crosses a specified threshold, at which point it is treated as  `fixed`  positioned.

#### Using CSS to draw a triangular
1) start with a rectangle.
2) Then adding border, and giving diffrent colors to the four borders(border-top)
3) decrease the width and height of the element to 0. Now the graph looks like a four triangles
4) Then remove one of the border and set the other two into transparent.

#### clearing techniques
-   Empty  `div`  method -  `<div style="clear:both;"></div>`.
-   Clearfix method - Refer to the  `.clearfix`  class above.

The  `.clearfix`  hack uses a clever CSS  [pseudo selector](https://github.com/yangshun/front-end-interview-handbook/blob/master/contents/en/css-questions.md#describe-pseudo-elements-and-discuss-what-they-are-used-for)  (`:after`) to clear floats. Rather than setting the overflow on the parent, you apply an additional class  `clearfix`  to it. Then apply this CSS:

.clearfix:after {
  content: ' ';
  visibility: hidden;
  display: block;
  height: 0;
  clear: both;
}
-   `overflow: auto`  or  `overflow: hidden`  method - Parent will establish a new block formatting context and expand to contains its floated children

#### Explain CSS sprites, and how you would implement them on a page or site.
CSS sprites combine multiple images into one single larger image.
Each image would have a corresponding CSS class with `background-image`, `background-position` and `background-size` properties defined.
Reduce the number of HTTP requests for multiple images (only one single request is required per spritesheet). But with HTTP2, loading multiple images is no longer much of an issue.

#### What are the different ways to visually hide content (and make it available only for screen readers)?
-   `width: 0; height: 0`. Make the element not take up any space on the screen at all, resulting in not showing it.
-   `position: absolute; left: -99999px`. Position it outside of the screen. 
-   `text-indent: -9999px`. This only works on text within the  `block`  elements.

#### Have you ever used a grid system, and if so, what do you prefer?
CSS Grid Layout is the most powerful layout system available in CSS. It is a **2-dimensional system**, meaning it can handle both columns and rows, unlike [flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) which is largely a 1-dimensional system. You work with Grid Layout by applying CSS rules both to a parent element (which becomes the Grid Container) and to that element’s children (which become Grid Items).

[Ref](https://css-tricks.com/snippets/css/complete-guide-grid/)
Grid container (parent)
-display, grid-template-columns/rows, grid-template-areas, grid gap, jsutify-content
Grid items (childern)
-grid-column-start, grid-column-end, grid-row-start, grid-row-end

#### Can you give an example of an @media property other than screen?
-   `all`  - for all media type devices
-   `print`  - for printers
-   `speech`  - for screenreaders that "reads" the page out loud
-   `screen`  - for computer screens, tablets, smart-phones etc

#### Describe pseudo-elements and discuss what they are used for
A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They can be used for decoration (`:first-line`,  `:first-letter`) or adding elements to the markup (combined with  `content: ...`) without having to modify the markup (`:before`,  `:after`).

-   `:first-line`  and  `:first-letter`  can be used to decorate text.
-   Used in the  `.clearfix`  hack as shown above to add a zero-space element with  `clear: both`.
-   Triangular arrows in tooltips use  `:before`  and  `:after`. Encourages separation of concerns because the triangle is considered part of styling and not really the DOM.

### layout example
实现一个两栏布局，左边为一段文字，两到三行，右边是一张图片，宽高固定，左边文字相对图片上下居中，图片贴着右边，文字占据剩余宽度。

 - [x] Felx
 [Notes](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
 - container
	 - flex-direction 主轴方向 排列方向
	 - flex-wrap 排不下如何换行
	 - flex-flow = flex-warp + flex-direction
	 - justify-content 主轴的对齐方式
	 flex-start, flex-end, center, space-between
	 - align-items 交叉轴对齐方式
	 flex-start, flex-end, center, stretch, baseline(项目第一行文字对齐)
	 - align-content 多条轴线对齐方式
 - items
	 - order 升序排列
	 - flex-grow default 0, 存在剩余空间也不放大
	 - flex-shrink default 1, 即空间不足， 项目将缩小
	 - flex-basis 在分配多余空间之前，项目占据的主轴空间（main size）default auto, 可以赋值
 - [x] Flex layout example
 - Does [Example](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)
```
<div class="box">
  <span class="item"></span>
</div>
```
上面代码中，div元素（代表骰子的一个面）是Flex容器，span元素（代表一个点）是Flex项目。如果有多个项目，就要添加多个span元素，以此类推。
`justify-content`, `align-items`
`flex-direction` `item:nth-child(n)`
`algin-self` `flex-wrap`

```HTML
<div class="box">
  <div class="row">
    <span class="item"></span>
    <span class="item"></span>
    <span class="item"></span>
  </div>
  <div class="row">
    <span class="item"></span>
  </div>
  <div class="row">
     <span class="item"></span>
     <span class="item"></span>
  </div>
</div>
```

```CSS
.box {
  display: flex;
  flex-wrap: wrap;
}

.row{
  flex-basis: 100%;
  display:flex;
}

.row:nth-child(2){
  justify-content: center;
}

.row:nth-child(3){
  justify-content: space-between;
}
```
* Holy Grail Layout
```HTML
<body class="HolyGrail">
  <header>...</header>
  <div class="HolyGrail-body">
    <main class="HolyGrail-content">...</main>
    <nav class="HolyGrail-nav">...</nav>
    <aside class="HolyGrail-ads">...</aside>
  </div>
  <footer>...</footer>
</body>
```

```css
.HolyGrail {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

header,
footer {
  flex: 1;
}

.HolyGrail-body {
  display: flex;
  flex: 1;
}

.HolyGrail-content {
  flex: 1;
}

.HolyGrail-nav, .HolyGrail-ads {
  /* 两个边栏的宽度设为12em */
  flex: 0 0 12em;
  //flex-grow, flex-shrink, flex-basis
}

.HolyGrail-nav {
  /* 导航放到最左边 */
  order: -1;
}
```
如果是小屏幕，躯干的三栏自动变为垂直叠加
```css
@media (max-width: 768px) {
  .HolyGrail-body {
    flex-direction: column;
    flex: 1;
  }
  .HolyGrail-nav,
  .HolyGrail-ads,
  .HolyGrail-content {
    flex: auto;
  }
}
```

 - [x] Three colunm to one colunm
 [Example](https://www.w3schools.com/css/tryit.asp?filename=trycss_website_layout_grid)
```
@media screen and (max-width: 600px) {  
	.column  {  
	width:  100%;  
	}  
}
```
 - [x] responsive websit layout
 [Example](https://www.w3schools.com/css/tryit.asp?filename=trycss_website_layout_blog)
* CSS 中的unit （这个我看了好多遍了 这次真的是最后一次！）
em: Relative to the front-size of the element
rem: Relative to the front-size of the root element
vw: relative to the 1% of the width of the viewport
vh: relative to the 1% of the height of the viewpoint
vmin: relative to 1% of viewpoint's smaller dimension
vmax: relative to 1% of the viewpoint's larger dimension
%: relative to the parent element
 - [x] 清除浮动
 ```
.row:after {
  content: "";
  display: table;
  clear: both;
}
```
 - [x] Centering
[Ref](https://css-tricks.com/centering-css-complete-guide/)
[水平](https://www.jianshu.com/p/b74689ee1eac)
inblock `text_align: center`
block `margin: 0 auto`
`justify-content: center`
[垂直](https://www.jianshu.com/p/086364d3d5e2)
inline `vertical-align`
line-height
```html
<div id="parent">
    <img src="image.png" alt="" />
</div>
```

```css
#parent { 
    line-height: 200px;
}

#parent img {
    vertical-align: middle;
}
```
flex `item-align: center`

### Transition 过渡动画
通过值的改变触发动画
[notes](https://www.w3schools.com/css/css3_transitions.asp)
```example
div {
  width: 100px;
  height: 100px;
  background: blue;
  transition: width 2s, background 1s;
}
div:hover {
  background: orange;
  width: 300px;
}
```
#### `transition: property duration timing-function delay`
### Animation 关键帧动画
与 transition 不同的是，他可以让元素自己动，而不要求某值的改变来触发动画
when we specify CSS styles inside the `@keyframes` rule, the animation will gradually change form current style to the new style at certain times
```example
<!DOCTYPE html>
<html>
<head>
<style>
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;
}

@keyframes example {
  0%   {background-color: red;}
  25%  {background-color: yellow;}
  50%  {background-color: blue;}
  100% {background-color: green;}
}
</style>
</head>
<body>

<p><b>Note:</b> This example does not work in Internet Explorer 9 and earlier versions.</p>

<div></div>

</body>
</html>
```
Also, we can change both the background and position of the element
```example
<!DOCTYPE html>
<html>
<head>
<style> 
div {
  width: 100px;
  height: 100px;
  background-color: red;
  position: relative; //should be a relative position
  animation-name: example;
  animation-duration: 4s;
}

@keyframes example {
  0%   {background-color:red; left:0px; top:0px;}
  25%  {background-color:yellow; left:200px; top:0px;}
  50%  {background-color:blue; left:200px; top:200px;}
  75%  {background-color:green; left:0px; top:200px;}
  100% {background-color:red; left:0px; top:0px;}
}
</style>
</head>
<body>

<p><b>Note:</b> This example does not work in Internet Explorer 9 and earlier versions.</p>

<div></div>

</body>
</html>
```
Negative values are also allowed. If using negative values, the animation will start as if it had already been playing for _N_ seconds. And this means, it will start at a specific completion rate relative to the `animation-delay`
 * `animation-iteration-count` specifies the number of times an animation should run. If it set to infinite, it will run forever
 * `animation-direction` shows the direction whether an animation should be played. we have `normal`, `reverse`, `alternate`, `alternate-reverse`
 * `animation-timing-function` specfies the speed curve of the animation, we have,

	 * ease - Specifies an animation with a slow start, then fast, then end slowly (this is default) 
	 * linear - Specifies an animation with the same speed from start to end 
	 * ease-in - Specifies an animation with a  slow start 
	 * ease-out - Specifies an animation with a slow end
	 * ease-in-out -Specifies an animation with a slow start and end 
	 * cubic-bezier(n,n,n,n) - Lets you define your own values in a cubic-bezier function

* `animation-fill-mode`  specify a style for the target element when the animation _is not playing_
we have, `none`, `forward`-remains last keyframe, `backward`-remains first keyframe, `both`

#### `animation: name duration timing-function delay iteration-count direction`

### CSS 逐帧动画
关键帧之间是有补间的，会选一个效果过渡过去，而逐帧动画则是每个 keyframe 之间没有过渡，直接切换过去; 逐帧需要有状态变化
`animation-timing-function: steps(n, jumpterm)`
For example, if _n_ is 5, there are 5 steps. Whether the animation holds temporarily at 0%, 20%, 40%, 60% and 80%, on the 20%, 40%, 60%, 80% and 100%, or makes 5 stops between the 0% and 100% along the animation, or makes 5 stops including the 0% and 100% marks (on the 0%, 25%, 50%, 75%, and 100%) depends on which of the following jump terms is used:
`jump-start`, `jump-end`, `jump-both`

### CSS Transform
[Document](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)
[Document1](https://www.w3schools.com/cssref/css3_pr_transform.asp)
`transform: none|transform-functions|initial|inherit`
`transform:rotate(100deg)` clockwise, using center point as rotation base;
`transform:matrix(n,n,n,n,n,n)`matrix( scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY() )
`transform:translateX(x)` using the value only for the x-axis (左右动)
`transform:scale(x,y)` 按照比例扩大缩小
`transform:scaleX(x)` center axis 扩大缩小
`transform:inherit` Inherits this property from its parent element.

### CSS Centering
[Ref](https://css-tricks.com/centering-css-complete-guide/) This ref includes a lot info.

#### [水平](https://www.jianshu.com/p/b74689ee1eac)
inblock `text_align: center`
block  分成定宽和不定宽两个情况
* 定宽 `margin: 0 auto`
* 不定宽 `position: absolute; transform: translateX(-50%);`
flex `justify-content: center`

#### [垂直](https://www.jianshu.com/p/086364d3d5e2)
* inline `vertical-align` 只对inline-element起作用
* display:table-cell
```
<style type="text/css">
    .father{
        width: 200px;
        height: 200px;
        background-color: red;
        display: table-cell;
        vertical-align: middle;
        text-align: center;
    }
    .child{
        width: 100px;
        height: 100px;
        background-color: green;
        display: inline-block;
        vertical-align: middle;
    }
</style>
<div class="father">
	<div class="child">我是个居中的盒子</div>
</div>
```
* position+margin
```
<style>
    .father{
        width: 200px;
        height: 200px;
        background-color: red;
        position: relative;
    }
    .child{
        position: absolute;
        width: 100px;
        height: 100px;
        background-color: green;
        margin: auto;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
    }
</style>
<div class="father">
	<div class="child">我是个居中的盒子</div>
</div>
```
* pure position
```
<style>
    .father{
        width: 500px;
        height: 300px;
        background-color: red;
        position: relative;
    }
    .child{
        /*如何让一个绝对定位的垂直居中： top设置50%，margin-top设置当前盒子的一半，并且是负*/
        position: absolute;
        width: 100px;
        height: 140px;
        background-color: green;
        left: 50%;
        margin-left: -50px;
        top: 50%;
        margin-top: -70px;
    }
</style>
<div class="father">
	<div class="child">我是个居中的盒子</div>
</div>

```
* flex `item-align: center`
