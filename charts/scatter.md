# 离散图(Scatter Chart)

散点图基于基本折线图，x 轴更改为线性轴。要使用散点图，数据必须作为包含 X 和 Y 属性的对象传递。下面的例子创建了一个 3 点的散点图。

```javascript
var scatterChart = new Chart(ctx, {
	type: "scatter",
	data: {
		datasets: [
			{
				label: "Scatter Dataset",
				data: [
					{
						x: -10,
						y: 0
					},
					{
						x: 0,
						y: 10
					},
					{
						x: 10,
						y: 5
					}
				]
			}
		]
	},
	options: {
		scales: {
			xAxes: [
				{
					type: "linear",
					position: "bottom"
				}
			]
		}
	}
});
```

## 数据集属性

散点图支持与[折线图(line chart)(./line.md#dataset-properties)]相同的所有属性。

## 数据结构

与可以以两种不同格式提供数据的折线图不同，散点图只接受点格式的数据。

```javascript
data: [
	{
		x: 10,
		y: 20
	},
	{
		x: 15,
		y: 10
	}
];
```
