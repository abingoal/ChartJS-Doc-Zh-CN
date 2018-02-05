# 坐标轴标记

创建图表时，您需要告诉查看者查看哪些数据。要做到这一点，你需要在坐标轴上做一些标签。

## 刻度标题配置

刻度标签配置在`scaleLabel`的配置下。它定义了刻度标题的选项。需要注意，这仅适用于笛卡尔坐标轴。

| 名称          | 类型      | 默认值                                                 | 描述                                                                                                  |
| ------------- | --------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| `display`     | `Boolean` | `false`                                                | 如果为 true，则显示轴标题                                                                             |
| `labelString` | `String`  | `''`                                                   | 标题的文字 (例如 "# of People" or "Respone Choices").                                                 |
| `fontColor`   | Color     | `'#666'`                                               | 刻度标题颜色                                                                                          |
| `fontFamily`  | `String`  | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 刻度标题字体，遵循 CSS font-family 选项。 (例如"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"） |
| `fontSize`    | `Number`  | `12`                                                   | 刻度标题文字大小                                                                                      |
| `fontStyle`   | `String`  | `'normal'`                                             | 刻度标题字体类型 遵循 CSS font-style 选项 (例如 normal, italic, oblique, initial, inherit)            |

## 创建自定义刻度格式

通常要更改刻度标记以包含有关数据类型的信息。例如，添加一个美元符号（'$'）。为此，需要重写轴配置中的 `ticks.callback` 方法。

在以下示例中，在 Y 轴的每个标签前显示一个美元符号。

如果回调函数返回 `null` 或`undefined`，则关联的网格线将被隐藏。

```javascript
var chart = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		scales: {
			yAxes: [
				{
					ticks: {
						// 在ticks中包含一个美元符号
						callback: function(value, index, values) {
							return "$" + value;
						}
					}
				}
			]
		}
	}
});
```
