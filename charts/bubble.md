# 气泡图(Bubble Chart)

气泡图用于同时显示三维数据。气泡的位置由前两个维度以及相应的水平和垂直轴线确定。第三个维度由单个气泡的大小来表示。

{% chartjs %}
{
"type": "bubble",
"data": {
"datasets": [{
"label": "First Dataset",
"data": [{
"x": 20,
"y": 30,
"r": 15
}, {
"x": 40,
"y": 10,
"r": 10
}],
"backgroundColor": "rgb(255, 99, 132)"
}]
},
}
{% endchartjs %}

## 示例用法

```javascript
// For a bubble chart
var myBubbleChart = new Chart(ctx, {
	type: "bubble",
	data: data,
	options: options
});
```

## 数据集属性

气泡图允许为每个数据集指定许多属性。这些用于设置特定数据集的显示属性。

所有属性，除了`label`可以被指定为一个数组。如果这些设置为数组值，则第一个值应用于数据集中的第一个气泡，第二个值应用于第二个气泡，依此类推。

| 名称                   | 类型              | 描述                               |
| ---------------------- | ----------------- | ---------------------------------- |
| `label`                | `String`          | 图例和工具提示中的数据集的标签名。 |
| `backgroundColor`      | `Color/Color[]`   | 气泡填充色                         |
| `borderColor`          | `Color/Color[]`   | 气泡边框色                         |
| `borderWidth`          | `Number/Number[]` | 气泡边框宽度(以像素为单位)         |
| `hoverBackgroundColor` | `Color/Color[]`   | 鼠标悬浮时气泡背景色               |
| `hoverBorderColor`     | `Color/Color[]`   | 鼠标悬浮时边框背景色               |
| `hoverBorderWidth`     | `Number/Number[]` | 鼠标悬浮时边框宽度                 |
| `hoverRadius`          | `Number/Number[]` | 鼠标悬停时气泡增加半径             |

## 配置选项

气泡图没有独特的配置选项。要配置所有气泡通用的选项，使用[点元素选项](../configuration/elements/point.md#point-configuration)。

## 默认选项

我们也可以更改气泡图表类型的默认值。这样做会使所有在这个点之后创建的气泡图表成为新的默认值。气泡图的默认配置可以在`Chart.defaults.bubble`中访问。

## 数据结构

对于气泡图，数据集需要包含一组数据点。每个点必须实现[气泡数据对象](#bubble-data-object)接口。

### 气泡数据对象

气泡图的数据以对象的形式传递。该对象必须实现以下接口。请注意，半径属性`r` **不会**被图表缩放。它是在 canvas 上绘制的气泡的像素的原始半径。

```javascript
{
    // X Value
    x: <Number>,

    // Y Value
    y: <Number>,

    // 气泡半径，不可缩放
    r: <Number>
}
```
