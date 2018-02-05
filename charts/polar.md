# 极地图(Polar Area)

极地面积图类似于饼图，但每个线段具有相同的角度 - 线段的半径因值而异。

当我们想要显示类似于饼图的比较数据，同时也要显示上下文的值的范围时通常使用这种类型的图表。

{% chartjs %}
{
"type": "polarArea",
"data": {
"labels": [
"Red",
"Green",
"Yellow",
"Grey",
"Blue"
],
"datasets": [{
"label": "My First Dataset",
"data": [11, 16, 7, 3, 14],
"backgroundColor": [
"rgb(255, 99, 132)",
"rgb(75, 192, 192)",
"rgb(255, 205, 86)",
"rgb(201, 203, 207)",
"rgb(54, 162, 235)"
]
}]
},
}
{% endchartjs %}

## 示例用法

```javascript
new Chart(ctx, {
	data: data,
	type: "polarArea",
	options: options
});
```

## 数据集属性

| 名称                   | 类型       | 描述                                                    |
| ---------------------- | ---------- | ------------------------------------------------------- |
| `label`                | `String`   | 在图例和工具提示中要显示数据集的标签                    |
| `backgroundColor`      | `Color[]`  | 填充色 参考 [颜色(Colors)](../general/colors.md#colors) |
| `borderColor`          | `Color[]`  | 边框色 参考 [颜色(Colors)](../general/colors.md#colors) |
| `borderWidth`          | `Number[]` | 边框宽度                                                |
| `hoverBackgroundColor` | `Color[]`  | 鼠标悬浮时背景色                                        |
| `hoverBorderColor`     | `Color[]`  | 鼠标悬浮时边框色                                        |
| `hoverBorderWidth`     | `Number[]` | 鼠标悬浮时边框宽度                                      |

## 配置选项

这些是特定于极地图的自定义选项。这些选项与[全局图表配置](#global-chart-configuration)选项合并，组成图表的最终选项。

| 名称                      | 类型      | 默认值           | 描述                                                                             |
| ------------------------- | --------- | ---------------- | -------------------------------------------------------------------------------- |
| `startAngle`              | `Number`  | `-0.5 * Math.PI` | 数据集中的第一个项目绘制时的起始角度                                             |
| `animation.animateRotate` | `Boolean` | `true`           | 如果为 true，则图表将使用旋转动画进行动画。该属性位于`options.animation`对象中。 |
| `animation.animateScale`  | `Boolean` | `true`           | 如果为 true，则显示从中心向外缩放图表的动画。                                    |

## 默认选项

我们还可以为每个创建的极地图类型更改这些默认值，该对象在 `Chart.defaults.polarArea` 处可用。更改全局选项只会影响更改后创建的图表。现有图表不会更改。

例如，要使用`animateScale = false`配置所有新的极地图，可以这么做：

```javascript
Chart.defaults.polarArea.animation.animateScale = false;
```

## 数据结构

对于极地图，数据集需要包含一组数据点。数据点应该是一个数字，Chart.js 将统计所有的数字并计算每个数字的相对比例。你还需要指定一个标签数组，以便 tooltips 正确显示每段数据。

```javascript
data = {
	datasets: [
		{
			data: [10, 20, 30]
		}
	],

	// 悬停不同弧线时，这些标签出现在图例和工具提示中
	labels: ["Red", "Yellow", "Blue"]
};
```
