# 混合图表(Mixed Chart Types)

Chart.js 可以创建两个或更多不同图表类型组合的混合图表。一个常见的例子是一个条形图和折线图的结合。

创建混合图表从一个基本图表的初始化开始。

```javascript
var myChart = new Chart(ctx, {
	type: "bar",
	data: data,
	options: options
});
```

现在我们有一个标准的条形图。现在我们需要将其中一个数据集转换为折线图数据集。

```javascript
var mixedChart = new Chart(ctx, {
	type: "bar",
	data: {
		datasets: [
			{
				label: "Bar Dataset",
				data: [10, 20, 30, 40]
			},
			{
				label: "Line Dataset",
				data: [50, 50, 50, 50],

				// 将此数据集类型变为折线图
				type: "line"
			}
		],
		labels: ["January", "February", "March", "April"]
	},
	options: options
});
```

如下有一个图表，呈现我们想要的信息。需要注意的是，在这种情况下折线图的默认选项不会合并。只有当`type`字段指定的类型时，默认类型的选项才会被合并。

{% chartjs %}
{
"type": "bar",
"data": {
"labels": [
"January",
"February",
"March",
"April"
],
"datasets": [{
"label": "Bar Dataset",
"data": [10, 20, 30, 40],
"borderColor": "rgb(255, 99, 132)",
"backgroundColor": "rgba(255, 99, 132, 0.2)"
}, {
"label": "Line Dataset",
"data": [50, 50, 50, 50],
"type": "line",
"fill": false,
"borderColor": "rgb(54, 162, 235)"
}]
},
"options": {
"scales": {
"yAxes": [{
"ticks": {
"beginAtZero": true
}
}]
}
}
}
{% endchartjs %}
