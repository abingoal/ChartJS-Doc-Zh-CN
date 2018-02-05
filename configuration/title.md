# 标题

图表标题定义要在图表顶部绘制的文本。

## 标题配置

标题在`options.title`中配置。图表标题的全局选项在`Chart.defaults.global.title`中定义。

| 名称         | 类型      | 默认值                                                 | 描述                         |
| ------------ | --------- | ------------------------------------------------------ | ---------------------------- |
| `display`    | `Boolean` | `false`                                                | 是否显示标题                 |
| `position`   | `String`  | `'top'`                                                | 标题未知[更多...](#position) |
| `fontSize`   | `Number`  | `12`                                                   | 字体大小                     |
| `fontFamily` | `String`  | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 字体集                       |
| `fontColor`  | Color     | `'#666'`                                               | 字体颜色                     |
| `fontStyle`  | `String`  | `'bold'`                                               | 字体样式                     |
| `padding`    | `Number`  | `10`                                                   | 标题文本上下方间距           |
| `text`       | `String`  | `''`                                                   | 标题文字                     |

### 未知

可用的标题位置为:

* `'top'`
* `'left'`
* `'bottom'`
* `'right'`

## 示例代码

以下示例将在创建的图表上加上“Custom Chart Title”的标题。

```javascript
var chart = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		title: {
			display: true,
			text: "Custom Chart Title"
		}
	}
});
```
