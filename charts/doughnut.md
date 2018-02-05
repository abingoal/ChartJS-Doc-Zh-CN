# 环形&饼图(Doughnut and Pie)

饼图和环形图表可能是最常用的图表。它们被分成不同的部分，每个部分的圆弧表示每个数据的比例值。

该图表在展示数据之间的关系比例方面非常出色。

饼图和环形图在 Chart.js 中实际上是同一个类，但有一个不同的默认值 - `cutoutPercentage`。意味着内部的百分比被减少。饼图默认为 `0`，甜甜圈默认为 `50`。

该图表在`Chart`核心中注册了两个别名。除了不同的默认值和不同的别名，其他是完全一样的。

{% chartjs %}
{
"type": "doughnut",
"data": {
"labels": [
"Red",
"Blue",
"Yellow",
],
"datasets": [{
"label": "My First Dataset",
"data": [300, 50, 100],
"backgroundColor": [
"rgb(255, 99, 132)",
"rgb(54, 162, 235)",
"rgb(255, 205, 86)",
]
}]
},
}
{% endchartjs %}

## 示例用法

```javascript
// 饼形图
var myPieChart = new Chart(ctx, {
	type: "pie",
	data: data,
	options: options
});
```

```javascript
// 环形图
var myDoughnutChart = new Chart(ctx, {
	type: "doughnut",
	data: data,
	options: options
});
```

## 数据集属性

环形/饼图允许为每个数据集指定多个属性以显示特定数据集。

| 名称                   | 类型       | 描述                                                                          |
| ---------------------- | ---------- | ----------------------------------------------------------------------------- |
| `label`                | `String`   | 图例和提示中显示的标签名                                                      |
| `backgroundColor`      | `Color[]`  | 数据集中每个数据区域的填充色 参考 [颜色(Colors)](../general/colors.md#colors) |
| `borderColor`          | `Color[]`  | 边框色 参考 [颜色(Colors)](../general/colors.md#colors)                       |
| `borderWidth`          | `Number[]` | 边框宽度                                                                      |
| `hoverBackgroundColor` | `Color[]`  | 鼠标悬浮时的填充色                                                            |
| `hoverBorderColor`     | `Color[]`  | 鼠标悬浮时边框色                                                              |
| `hoverBorderWidth`     | `Number[]` | 鼠标悬浮时边框宽度                                                            |

## 配置选项

这些是 Pie＆Donut 图表特有的自定义选项。这些选项与全局图表配置选项合并，组成最终选项。

| 名称                      | 类型      | 默认值                             | 描述                                                                           |
| ------------------------- | --------- | ---------------------------------- | ------------------------------------------------------------------------------ |
| `cutoutPercentage`        | `Number`  | `50` - for doughnut, `0` - for pie | 从中间切出的图表的百分比。                                                     |
| `rotation`                | `Number`  | `-0.5 * Math.PI`                   | 起始角度                                                                       |
| `circumference`           | `Number`  | `2 * Math.PI`                      | 允许图形覆盖                                                                   |
| `animation.animateRotate` | `Boolean` | `true`                             | 如果为 true，则图表将使用旋转动画进行动画。该属性在`options.animation`对象中。 |
| `animation.animateScale`  | `Boolean` | `false`                            | 如果为 true，则将动画从中心向外缩放图表。                                      |

## 默认选项

我们也可以为创建的每个环形图表更改这些默认值，该配置选项在`Chart.defaults.doughnut`中可用。饼图还可以在`Chart.defaults.pie`中使用同样的值，唯一的区别是`cutoutPercentage`被设置为 0。

## 数据结构

对于饼图，数据集需要包含一组数据点。数据点应该是一个数字，Chart.js 将所有的数字汇总并计算每个数据的相对比例。

你还需要指定一个标签数组，以便在 tooltips 中显示

```javascript
data = {
	datasets: [
		{
			data: [10, 20, 30]
		}
	],

	// These labels appear in the legend and in the tooltips when hovering different arcs
	labels: ["Red", "Yellow", "Blue"]
};
```
