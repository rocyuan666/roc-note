## **把父盒子设置成弹性盒布局：**
display: flex;
特征：子元素默认水平排列。
## **Flex方向属性：**
flex-direction:row | column | column-reverse | inherit | row-reverse

- row（默认）：主轴为水平方向，起点在左端。
- row-reverse：主轴为水平方向，起点在右端。
- column（常用）：主轴为垂直方向，起点在上沿。
- column-reverse：主轴为垂直方向，起点在下沿。
## **Flex对齐方式：**
主轴对齐：
justify-content:flex-start | flex-end | center | space-between | space-around;

- flex-start（默认值）：左对齐
- flex-end：右对齐
- center（常用）： 居中
- space-between：两端对齐，子元素之间的间隔都相等。
- space-around：每个子元素两侧的间隔相等。所以，子元素之间的间隔比子元素与边框的间隔大一倍。

交叉轴对齐：
align-items:flex-start | flex-end | center | baseline | stretch;

- flex-start：交叉轴的起点对齐。
- flex-end：交叉轴的终点对齐。
- center（常用）：交叉轴的中点对齐。
- baseline: 项目的第一行文字的基线对齐。
- stretch（默认值）：如果子元素未设置高度或设为auto，将占满整个容器的高度。
## **Flex换行：**
flex-wrap: nowrap | wrap | wrap-reverse;

- nowrap（默认）：不换行。
- wrap（常用）：换行，第一行在上方。
- wrap-reverse：换行，第一行在下方。
## **常用属性属性值：**
display: flex; — 设置flex容器
flex-direction: column; — 容器内元素竖着排列
justify-content: center; — 容器内元素主轴对齐
align-items: center; — 容器内元素交叉轴对齐
flex-wrap: wrap; — 容器内元素换行
