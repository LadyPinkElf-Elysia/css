# CSS
## 核心功能

### 尺寸操作

- `width` 宽度
    可以控制元素的宽度，单位有像素`px`,百分比`%`等等
    默认值是`auto`，块级元素宽度自动撑满父容器
    也可以限定最大`max-width`和最小`min-width`
    ```css
    .box{
        width:500px; /* 或用百分比 */
    }
    ```
- `height` 高度
    可以控制元素的高度，单位有像素`px`,百分比`%`等等
    默认值是`auto`，块级元素高度由内容撑开
    也可以限定最大`max-height`和最小`min-height`
    ```css
    .box{
        height:500px; /* 或用百分比 */
    }
    ```
- `border` 边框
    可以控制元素的边框
    第一个参数是边框宽度`border-width`（可单独设置）
    第二个参数是边框样式`border-style`（默认为`none`，可单独设置），常见的选项为：
    |选项值|释义|
    |:--|:--|
    |`none`|无边框|
    |`solid`|单实线|
    |`dashed`|虚线|
    |`dotted`|点线|
    |`double`|双实线|

    第三个参数是边框颜色，可以用颜色英文名称，或者十六进制颜色值，RGB颜色值（R是红色，G是绿色，B是蓝色）

    ```css
    .box{
        border:1px dotted grey; 
        /*边框宽度 边框样式 边框颜色*/
    }
    ```
- `border-radius` 边框圆角
    可以控制边框的圆角
    ```css
    .box{
        border-radius:8px; 
        /*以8px为半径画圆使得该圆内切于边框，则圆弧为边框的圆角*/
    }
    ```
- `padding` 内边距
    可以控制边框和内容之间的距离
    如果仅有一个参数，那么表示四个方向的距离均为该值
    如果有两个参数，那么第一个值表示上下，第二个值表示左右
    如果有三个参数，那么第一个值表示上，第二个值表示左右，第三个值表示下
    如果有四个参数，那么第一个值表示上，第二个值表示右，第三个值表示下，第四个值表示左（从上开始，顺时针转）
    上述规则为**值复制原则**
    |值个数|值表示|
    |:--|:--|
    |1|上下左右|
    |2|上下 左右|
    |3|上 左右 下|
    |4|上 右 下 左|

    ```css
    .box{
        padding: 15px;                    
        /* 四边都是 15px */
        padding: 10px 20px;               
        /* 上下 10px，左右 20px */
        padding: 10px 20px 30px;          
        /* 上 10px，左右 20px，下 30px */
        padding: 10px 20px 30px 40px;     
        /* 上 10px，右 20px，下 30px，左 40px */
    }
    ```
    也可以直接指定单边，可读性较好，`padding-top`(上),`padding-right`(右),`padding-bottom`(下),`padding-left`(左)
    ```css
    .box{
        padding-top: 10px; /*上*/
        padding-right: 20px; /*右*/
        padding-bottom: 30px; /*下*/
        padding-left: 40px; /*左*/
    }
    ```
- `margin` 外边距
    可以控制边框外面和其他元素之间的距离，和`padding`差不多，参数也是值复制原则，也可以直接指定单边
    `margin`支持负值，`padding`不支持
    外边距合并：垂直相邻的两个块级元素，上下`margin`会取较大值，不是相加

    常用写法
    ```css
    .box{
        margin:0 auto; /*块级元素可以用这个实现水平居中,auto为自动计算*/
    }
    ```

- `box-sizing` 盒模型
    决定元素的`width`和`height`怎么算，有两个值：`content-box`(标准盒)、`border-box`(怪异盒)
    标准盒模型：`width` 只代表内容区的宽度。`padding` 和 `border` 会额外撑大元素
    怪异盒模型：`width` 代表边框盒的宽度，`padding` 和 `border` 从里面扣
    ```text
    content-box:
    ┌─────────────────────────────┐
    │ border 5px                  │
    │ ┌─────────────────────────┐ │
    │ │ padding 20px            │ │
    │ │ ┌─────────────────────┐ │ │
    │ │ │ content 200px       │ │ │
    │ │ └─────────────────────┘ │ │
    │ └─────────────────────────┘ │
    └─────────────────────────────┘
    总宽 = 200 + 40 + 10 = 250px

    border-box:
    ┌─────────────────────┐
    │ border 5px          │
    │ ┌─────────────────┐ │
    │ │ padding 20px    │ │
    │ │ ┌─────────────┐ │ │
    │ │ │ content 150 │ │ │
    │ │ └─────────────┘ │ │
    │ └─────────────────┘ │
    └─────────────────────┘
    总宽 = 200px
    ```

### 背景处理

- `background-color` 背景颜色
    可以控制元素背景的颜色
    ```css
    .box{
        background-color:#f9f9f9;
    }
    ```
- `background-image` 背景图片
    可以控制元素背景的图片，背景图会覆盖在背景色上方；图片透明或未铺满时，背景色会透出
    ```css
    .box{
        background-image:url(./bg.jpg); /*写图片地址*/
    }
    ```
- `box-shadow` 阴影效果
    可以控制元素的阴影效果
    第一个参数是元素的水平偏移，5px表示向右偏移5px
    第二个参数是元素的竖直偏移，5px表示向下偏移5px
    第三个参数是阴影晕染的模糊半径（边缘“羽化”），值越大，阴影边缘越柔和、越向外晕开
    第四个参数是阴影晕染的扩展半径（阴影“胖瘦”），正值：阴影在模糊之前先向外扩大，负值：阴影在模糊之前先向内收缩，默认为0
    第五个参数是阴影晕染的颜色
    第六个参数是`inset`，表示内阴影；不写`inset`就是外阴影
    ```css
    .box{
        box-shadow:5px 5px 5px grey;
        /* 水平偏移，竖直偏移，晕染宽度，晕染颜色*/
    }
    ```

### 文本处理

- `color` 文字颜色
    文字的颜色
    ```css
    .box{
        color:red;
    }
    ```
- `text-indent` 文字缩进
    可以控制文字的缩进
    ```css
    .box{
        text-indent:2em; /*em是当前元素的文字大小，可以自动计算*/
    }
    ```
- `text-align` 文字水平偏移
    可以控制文字的水平偏移，`center`是文字水平居中，`left`是文字水平居左，`right`是文字水平居右
    ```css
    .box{
        text-align:center;
    }
    ```
- `text-shadow` 文字阴影
    与`box-shadow`类似，可以实现艺术字的效果
- `text-decoration` 文字装饰
    可以控制文字的装饰效果
- `line-height` 行高
    可以控制多行文字之间的行间距，也影响单行文字的垂直居中
- `font-size` 字号
    可以控制文字的字号
- `font-family` 字体
    可以控制文字的字体
- `font-weight` 字重
    可以控制文字的粗细

### 定位

- `position` 定位模式
    可以控制定位的模式，有`static`(默认定位)，`absolute`(绝对定位)，`relative`(相对定位)，`fixed`(固定定位)，`sticky`(粘性定位)
    不能单独使用，要配合偏移值`top`(与顶部距离),`bottom`(与底部距离),`left`(与左边距离),`right`(与右边距离)
    
    - `static`是所有元素的默认定位，元素处于正常文档流，设置`top`/`right`/`bottom`/`left`无效，忽略`z-index`
    - `relative`是相对定位，参照物是元素自身的原始位置，不脱离文档流，视觉上移动，布局位置不变。可用于微调图标，作为绝对定位的定位祖先，创建`hover`(鼠标悬停在元素上)动效偏移，配合`z-index`调整层叠顺序
    - `absolute`是绝对定位，参照物是最近的position非static的祖先元素（有定位祖先就参照定位祖先，无就参照视口），脱离文档流，默认宽度由内容决定（除非指定宽度），可创建新的层叠上下文。可用于模态框，弹窗，下拉菜单，图标角标，自定义滚动条，轮播图指示器
    - `fixed`是固定定位，参照物是浏览器视口，脱离文档流，不随滚动条滚动，可用于导航栏，侧边栏，广告条
    - `sticky`是粘性定位，参照物是最近的滚动祖先，混合定位（`relative`和`fixed`），条件触发，达到阈值（需指定）后变为`fixed`，可用于表头固定，分类导航，阅读进度条

    | 定位类型 | 参照物 | 脱离文档流 | 视觉 vs 布局 | `top/right/bottom/left` | `z-index` | 典型用途 |
    |---|---|---|---|---|---|---|
    | `static` | 无（正常文档流） | 否 | 一致 | 无效 | 忽略 | 所有元素的默认值 |
    | `relative` | 元素自身原始位置 | 否 | 视觉移动，布局位置不变 | 有效 | 有效 | 微调图标、作为 absolute 的定位祖先、hover 偏移、调层叠顺序 |
    | `absolute` | 最近的非 static 祖先；没有则参照视口 | 是 | 完全脱离，不占原位置 | 有效 | 有效，可创建层叠上下文 | 模态框、弹窗、下拉菜单、图标角标、自定义滚动条、轮播指示器 |
    | `fixed` | 浏览器视口 | 是 | 不随滚动条滚动 | 有效 | 有效 | 固定导航栏、侧边栏、广告条 |
    | `sticky` | 最近的滚动祖先 | 否（阈值内仍占位） | 阈值内像 relative，超过阈值像 fixed | 有效（必须指定阈值） | 有效 | 表头固定、分类导航、阅读进度条 |

## 布局处理

### 弹性布局(Flex)

可利用这个网址[练习](https://flexboxfroggy.com/)

- `display`
    当使用弹性布局时，先把`display`的值改成`flex`(块级弹性容器)或者`inline-flex`(行内弹性容器)，使得子元素自动变成弹性项目
    ```css
    .box{
        display:flex;
    }
    ```

- `flex-direction` 主轴方向
    主轴：项目排列的主要方向
    交叉轴：垂直于主轴的轴
    ```css
    .container {
        flex-direction: row; /* 默认：左到右 */
        flex-direction: row-reverse; /* 右到左 */
        flex-direction: column; /* 上到下 */
        flex-direction: column-reverse; /* 下到上 */
    }
    ```
- `justify-content` 主轴对齐
    ```css
    .container {
        justify-content: flex-start; /* 默认：主轴起点对齐 */
        justify-content: flex-end; /* 主轴终点对齐 */
        justify-content: center; /* 主轴居中对齐 */
        justify-content: space-between; /* 两端对齐，项目间等距 */
        justify-content: space-around; /* 每个项目两侧等距 */
        justify-content: space-evenly; /* 项目与项目、项目与边界等距 */
    }
    ```

- `align-items` 交叉轴对齐
    作用于每一行中的单个项目，相当于为所有子项统一设置`align-self`(单个项目对齐，继承`align-items`)
    ```css
    .container {
        align-items: stretch; /* 默认 */
        align-items: flex-start; /* 交叉轴起点对齐 */
        align-items: flex-end; /* 交叉轴终点对齐 */
        align-items: center; /* 交叉轴居中对齐 */
        align-items: baseline; /* 基线对齐 */
    }
    .item {
        align-self: auto; /* 默认：继承align-items */
        align-self: flex-start;
        align-self: flex-end;
        align-self: center;
        align-self: baseline;
        align-self: stretch;
    }
    ```

- `align-content` 多轴线对齐
    将多行项目作为一个整体，在交叉轴上分配空间
    ```css
    .container {
        align-content: stretch; /* 默认：拉伸填满 */
        align-content: flex-start; /* 交叉轴起点对齐 */
        align-content: flex-end; /* 交叉轴终点对齐 */
        align-content: center; /* 交叉轴居中对齐 */
        align-content: space-between; /* 交叉轴两端对齐 */
        align-content: space-around; /* 交叉轴等距分布 */
    }
    ```

- `flex-wrap` 换行控制
    ```css
    .container {
        flex-wrap: nowrap; /* 默认：不换行 */
        flex-wrap: wrap; /* 换行，第一行在上 */
        flex-wrap: wrap-reverse; /* 换行，第一行在下 */
    }
    ```
- `flex-flow` 简写属性
    `flex-direction`和`flex-wrap`的简写属性，
    第一个参数是`flex-direction`
    第二个参数是`flex-wrap`
    ```css
    .container{
        display:flex;
        flex-flow:column wrap;
    }
    ```

- `flex` 简写属性
    第一个参数控制放大比例，默认为0，值为0时不放大，值为1就等分剩余空间（占比，从剩余空间可以占到的比例）
    第二个参数控制缩小比例，默认为1，值为0时空间不足不缩小，值为1时空间不足就等比例缩小（占比，从剩余空间可以占到的比例）
    第三个参数控制初始大小，配合第一个参数实现等分
    ```css
    .item {
        flex: none; /* 0 0 auto */
        flex: auto; /* 1 1 auto */
        flex: 1; /* 1 1 0% */
        flex: 0 0 200px; /* flex-grow flex-shrink flex-basis */
    }
    ```
- `order` 排列顺序
    ```css
    .item {
        order: 0; /* 默认：按文档流顺序 */
        order: 1; /* 数值越大，排列越靠后 */
        order: -1; /* 数值越小，排列越靠前 */
    }
    ```

### 网格布局(Grid)

- `display`
    当使用网格布局时，先把`display`的值改成`grid`(块级网格容器)或`inline-grid`(行内网格容器)
    ```css
    .container{
        display:grid
    }
    ```
- `grid-template-columns` 每一列的列宽
    - 有时候单元格的大小是固定的，但是容器的大小不确定。这时可以用`auto-fill`关键字表示自动填充。
    - 除了`auto-fill` ，还有一个关键字`auto-fit`，`auto-fill`会用空格子填满剩余宽度，`auto-fit`则会尽量扩大单元格的宽度。
    - 为了方便表示比例关系，网格布局提供了`fr`关键字，如果两列的宽度分别为1fr和2fr，就表示后者是前者的两倍
    - 也可以用`minmax`函数产生一个长度范围，接收两个参数，分别是最小值和最大值
    - `auto`关键字表示由浏览器自己决定长度
    - 可以使用方括号指定网格线的名字，方便引用
    ```css
    .container {
        display: grid;
        grid-template-columns: 100px 100px 100px;
        /* 可以用px*/
        grid-template-columns: 33.33% 33.33% 33.33%; 
        /* 也可以用百分比*/
        grid-template-columns: repeat(3, 33.33%);
        /* 可用repeat函数简化  repeat接收两个参数，第一个参数是重复的次数，第二个参数是所要重复的值*/
        grid-template-columns:  repeat(auto-fill, 100px);
        /* 上面表示每列宽度100px，然后自动填充，直到容器不能放置更多的列。*/
        grid-template-columns: 150px 1fr 2fr;
        /* fr可以与绝对长度的单位结合使用，这时会非常方便，上面表示：第一列的宽度为150像素，第二列的宽度是第三列的一半*/
        grid-template-columns: 1fr 1fr minmax(100px,1fr);
        /* 上面代码中，minmax(100px, 1fr)表示列宽不小于100px，不大于1fr*/
        grid-template-columns: 100px auto 100px;
        /* 上面代码中，第二列的宽度，基本上等于该列单元格的最大宽度，除非单元格内容设置了min-width，且这个值大于最大宽度。*/
        grid-template-columns: [c1] 100px [c2] 100px [c3];
    }
    ```

- `grid-template-rows` 每一行的行高
    和`grid-template-columns`属性类似

- `gap` 简写属性
    `gap`属性是`column-gap`(列间距)和`row-gap`(行间距)的合并简写形式，接受1-2个值
    ```css
    .container {
        gap: 20px;        /* 行间距和列间距都是 20px */
        gap: 10px 20px;   /* 行间距 10px，列间距 20px */
    }
    ```
- `grid-template-areas` 网格区域
    网格布局允许指定"区域"（area），一个区域由单个或多个单元格组成。
    ```css
    .container {
        display: grid;
        grid-template-columns: 100px 100px 100px;
        grid-template-rows: 100px 100px 100px;
        grid-template-areas: "header header header" "main main sidebar" "footer footer footer";
    }
    ```
- `grid-auto-flow` 
    划分网格以后，容器的子元素会按照顺序，自动放置在每一个网格。
    当属性值为`row`时，先行后列
    当属性值为`row dense`时，先行后列，尽可能填满空格
    当属性值为`column`时，先列后行
    当属性值为`column dense`时，先列后行，尽可能填满空格

- `place-items` 简写属性
    `place-items`属性是`align-items`属性和`justify-items`属性的合并简写形式，接受1-2个属性
    `justify-items`属性设置网格项目在单元格内的水平位置（左中右）
    `align-items`属性设置网格项目在单元格内的垂直位置（上中下）
    |属性值|释义|
    |:--|:--|
    |start|对齐单元格的起始边缘|
    |end|对齐单元格的结束边缘|
    |center|单元格内部居中|
    |stretch|拉伸，占满整个单元格（默认值）|

    ```css
    .container{
        place-items: center center;
        /* 第一个是align-items 第二个是justify-items */
    }
    ```
- `place-content` 简写属性
    `place-content`属性是`align-content`属性和`justify-content`属性的合并简写形式，接受1-2个属性
    `justify-content`属性是整个内容区域在容器里面的水平位置（左中右）
    `align-content`属性是整个内容区域的垂直位置（上中下）
    |属性值|释义|
    |:--|:--|
    |start|对齐容器的起始边框|
    |end|对齐容器的结束边框|
    |center|容器内部居中|
    |stretch|项目大小没有指定时，拉伸占据整个网格容器|
    |space-around|每个项目两侧的间隔相等，项目之间的间隔比项目与容器边框的间隔大一倍|
    |space-between|项目与项目的间隔相等，项目与容器边框之间没有间隔|

    ```css
    .container{
        place-content: center center;
        /* 第一个是align-content 第二个是justify-content */
    }
    ```
- `grid-auto-rows` 和 `grid-auto-columns`
    没有被显式地定义行高或列宽的网格元素，就需要使用`grid-auto-rows`和`grid-auto-columns`属性来指定它们的默认尺寸
    ```css
    .grid-container {
        display: grid;
        grid-auto-rows: 100px;
    }
    ```
- `grid-column` 和 `grid-row` 简写属性
    `grid-column`属性是`grid-column-start`和`grid-column-end`的合并简写形式
    `grid-row`属性是`grid-row-start`属性和`grid-row-end`的合并简写形式
    ```css
    /*1.指定为第几个网格线*/
    /*项目 item-1 占据第 1 行，从第 1 条列线到第 3 条列线（即跨第 1、2 列）*/
    .item-1 {
        grid-column: 1 / 3;
        grid-row: 1 / 2;
    }
    /* 等同于 */
    .item-1 {
        grid-column-start: 1;
        grid-column-end: 3;
        grid-row-start: 1;
        grid-row-end: 2;
    }
    /*2.也可以使用span关键字，表示跨越多少个网格。*/
    /*项目item-1占据的区域，包括第一行 + 第二行、第一列 + 第二列。*/
    .item-1 {
        background: #b03532;
        grid-column: 1 / 3;
        grid-row: 1 / 3;
    }
    /* 等同于 */
    .item-1 {
        background: #b03532;
        grid-column: 1 / span 2;
        grid-row: 1 / span 2;
    }
    /*3.斜杠以及后面的部分可以省略，默认跨越一个网格。*/
    /*项目item-1占据左上角第一个网格*/
    .item-1 {
        grid-column: 1;
        grid-row: 1;
    }
    ```
- `grid-area` 简写属性
    `grid-area`属性指定项目放在哪一个区域。
    ```css
    .item-1 {
        /*1号项目位于header区域*/
        grid-area: header;
    }
    ```
    `grid-area`属性还可用作`grid-row-start`、`grid-row-end`、`grid-column-start`、`grid-column-end`的合并简写形式，直接指定项目的位置。
    ```css
    /*示例：
    grid-area: <row-start> / <column-start> / <row-end> / 
    <column-end>;
    */
    .item-1 {
        grid-area: 1 / 1 / 3 / 3;
    }
    ```
- `place-self` 简写属性
    `place-self`属性是`align-self`属性和`justify-self`属性的合并简写形式，接受1-2个值
    `justify-self`属性设置单元格内容的水平位置（左中右），跟`justify-items`属性的用法完全一致，但只作用于单个项目。
    `align-self`属性设置单元格内容的垂直位置（上中下），跟`align-items`属性的用法完全一致，也是只作用于单个项目。
    |属性值|释义|
    |:--|:--|
    |start|对齐单元格的起始边缘|
    |end|对齐单元格的结束边缘|
    |center|单元格内部居中|
    |stretch|拉伸，占满整个单元格（默认值）|
    ```css
    .item{
        place-self: center center;
        /* 第一个是align-self 第二个是justify-self */
    }
    ```

