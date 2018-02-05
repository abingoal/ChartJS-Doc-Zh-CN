# 提示

## 提示配置

提示框配置在`options.tooltips`中设置。图表提示框的全局选项在`Chart.defaults.global.tooltips`中定义。

| 名称                 | 类型       | 默认值                                                 | 描述                                                                                      |
| -------------------- | ---------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| `enabled`            | `Boolean`  | `true`                                                 | 是否开启提示                                                                              |
| `custom`             | `Function` | `null`                                                 | 参阅[自定义工具](#custom-tooltips)提示部分 See                                            |
| `mode`               | `String`   | `'nearest'`                                            | 设置提示框中显示的元素 [更多...](../general/interactions/modes.md#interaction-modes).     |
| `intersect`          | `Boolean`  | `true`                                                 | 如果为 true，则提示框模式仅在鼠标位置与元素相交时才适用。如果为 false，该模式将随时应用。 |
| `position`           | `String`   | `'average'`                                            | 提示的位置. [更多...](#position-modes)                                                    |
| `callbacks`          | `Object`   |                                                        | 参考 [回调部分](#tooltip-callbacks)                                                       |
| `itemSort`           | `Function` |                                                        | 提示项目排序 [more...](#sort-callback)                                                    |
| `filter`             | `Function` |                                                        | 过滤提示项目. [more...](#filter-callback)                                                 |
| `backgroundColor`    | Color      | `'rgba(0,0,0,0.8)'`                                    | 背景色                                                                                    |
| `titleFontFamily`    | `String`   | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 标题字体                                                                                  |
| `titleFontSize`      | `Number`   | `12`                                                   | 标题字号                                                                                  |
| `titleFontStyle`     | `String`   | `'bold'`                                               | 标题样式                                                                                  |
| `titleFontColor`     | Color      | `'#fff'`                                               | 标题颜色                                                                                  |
| `titleSpacing`       | `Number`   | `2`                                                    | 添加到每个标题顶部和底部的内间距                                                          |
| `titleMarginBottom`  | `Number`   | `6`                                                    | 标题部分的下外间距                                                                        |
| `bodyFontFamily`     | `String`   | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 内容的字体                                                                                |
| `bodyFontSize`       | `Number`   | `12`                                                   | 内容字体大小                                                                              |
| `bodyFontStyle`      | `String`   | `'normal'`                                             | 内容字体样式                                                                              |
| `bodyFontColor`      | Color      | `'#fff'`                                               | 内容字体颜色                                                                              |
| `bodySpacing`        | `Number`   | `2`                                                    | 内容的上下内间距                                                                          |
| `footerFontFamily`   | `String`   | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 页脚字体(指提示框的底部，下同)                                                            |
| `footerFontSize`     | `Number`   | `12`                                                   | 页脚字体大小                                                                              |
| `footerFontStyle`    | `String`   | `'bold'`                                               | 页脚字体样式                                                                              |
| `footerFontColor`    | Color      | `'#fff'`                                               | 页脚字体颜色                                                                              |
| `footerSpacing`      | `Number`   | `2`                                                    | 页脚上下内间距                                                                            |
| `footerMarginTop`    | `Number`   | `6`                                                    | 页脚的外边距                                                                              |
| `xPadding`           | `Number`   | `6`                                                    | 提示框的左右内边距                                                                        |
| `yPadding`           | `Number`   | `6`                                                    | 提示框的上下内边距                                                                        |
| `caretPadding`       | `Number`   | `2`                                                    | 提示箭头                                                                                  |
| `caretSize`          | `Number`   | `5`                                                    | 提示箭头大小，单位:px                                                                     |
| `cornerRadius`       | `Number`   | `6`                                                    | 提示框圆角                                                                                |
| `multiKeyBackground` | Color      | `'#fff'`                                               | 当多个项目位于提示框中时，颜色会在彩色框后面绘制                                          |
| `displayColors`      | `Boolean`  | `true`                                                 | 如果为 true，则工具提示中会显示颜色框                                                     |
| `borderColor`        | Color      | `'rgba(0,0,0,0)'`                                      | 边框颜色                                                                                  |
| `borderWidth`        | `Number`   | `0`                                                    | 边框大小                                                                                  |

### 位置模式

提供的模式有:

* 'average'
* 'nearest'

'average' 模式将提示框放在工具提示中显示的项目的平均位置。

'nearest' 模式将提示框放在最接近事件位置的元素的位置。

可以通过向`Chart.Tooltip.positioners`映射添加函数来定义新模式。

### 排序回调

允许对[提示项](#chart-configuration-tooltip-item-interface)进行排序。必须至少实现一个可以传递给[Array.prototype.sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)的函数。此函数也可以接受传递给图表的数据对象的第三个参数。

### 过滤回调

允许过滤[提示项](#chart-configuration-tooltip-item-interface)。必须至少实现一个可以传递给[Array.prototype.filter](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)的函数。此函数也可以接受传递给图表的数据对象的第二个参数。

## 提示框回调

提示框标签的配置使用`callbacks`关键字嵌套在提示框下面。提示框具有以下提供文本的回调。对于所有函数，“this”是从`Chart.Tooltip`构造函数创建的提示对象。

使用相同的参数调用所有函数：一个[提示项](#chart-configuration-tooltip-item-interface)和传递给图表的数据对象。所有函数必须返回字符串或字符串数 ​​ 组。字符串的数组被视为多行文本。

| 名称           | 参数                       | 描述                                                      |
| -------------- | -------------------------- | --------------------------------------------------------- |
| `beforeTitle`  | `Array[tooltipItem], data` | 返回标题前要渲染的文字                                    |
| `title`        | `Array[tooltipItem], data` | 返回要作为提示框标题渲染的文本                            |
| `afterTitle`   | `Array[tooltipItem], data` | 返回标题后渲染的文本                                      |
| `beforeBody`   | `Array[tooltipItem], data` | 返回在内容部分之前渲染的文本                              |
| `beforeLabel`  | `tooltipItem, data`        | 返回在单个 label 之前渲染的文本。提示框中的每个项目调用   |
| `label`        | `tooltipItem, data`        | 返回在提示框中为单个项目渲染的文本                        |
| `labelColor`   | `tooltipItem, chart`       | 返回要渲染提示项目的颜色 [更多...](#label-color-callback) |
| `afterLabel`   | `tooltipItem, data`        | 返回在单个 label 之后渲染的文本                           |
| `afterBody`    | `Array[tooltipItem], data` | 返回在 body 部分后渲染的文本                              |
| `beforeFooter` | `Array[tooltipItem], data` | 返回在页脚部分之前渲染的文本                              |
| `footer`       | `Array[tooltipItem], data` | 返回纯文本的方式渲染页脚                                  |
| `afterFooter`  | `Array[tooltipItem], data` | 在页脚部分后面渲染的文字                                  |

### 标签颜色回调

例如要为工具提示中的每个项目返回一个红色框，可以执行以下操作：

```javascript
var chart = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		tooltips: {
			callbacks: {
				labelColor: function(tooltipItem, chart) {
					return {
						borderColor: "rgb(255, 0, 0)",
						backgroundColor: "rgb(255, 0, 0)"
					};
				}
			}
		}
	}
});
```

### 提示项接口

传递给工具提示回调的工具提示项实现了以下接口

```javascript
{
    // X 值
    xLabel: String,

    // Y 值
    yLabel: String,

    // 数据集的索引
    datasetIndex: Number,

    // 数据集中此数据的索引
    index: Number,

    // 匹配点的X位置
    x: Number,

    // 匹配点的Y位置
    y: Number,
}
```

## 外部工具提示(自定义)

自定义工具提示允许您使用钩子介入工具提示渲染过程，以便以自定义方式渲染工具提示。通常这是用来创建一个 HTML 提示，而不是一个 oncanvas。您可以在全局或图表配置中启用自定义工具提示，如下所示：

```javascript
var myPieChart = new Chart(ctx, {
	type: "pie",
	data: data,
	options: {
		tooltips: {
			custom: function(tooltipModel) {
				// 工具提示元素
				var tooltipEl = document.getElementById("chartjs-tooltip");

				// 在第一次渲染时创建元素
				if (!tooltipEl) {
					tooltipEl = document.createElement("div");
					tooltipEl.id = "chartjs-tooltip";
					tooltipEl.innerHTML = "<table></table>";
					document.body.appendChild(tooltipEl);
				}

				// 如果没有提示则隐藏
				if (tooltipModel.opacity === 0) {
					tooltipEl.style.opacity = 0;
					return;
				}

				// 插入符号的位置
				tooltipEl.classList.remove("above", "below", "no-transform");
				if (tooltipModel.yAlign) {
					tooltipEl.classList.add(tooltipModel.yAlign);
				} else {
					tooltipEl.classList.add("no-transform");
				}

				function getBody(bodyItem) {
					return bodyItem.lines;
				}

				// 设置文字
				if (tooltipModel.body) {
					var titleLines = tooltipModel.title || [];
					var bodyLines = tooltipModel.body.map(getBody);

					var innerHtml = "<thead>";

					titleLines.forEach(function(title) {
						innerHtml += "<tr><th>" + title + "</th></tr>";
					});
					innerHtml += "</thead><tbody>";

					bodyLines.forEach(function(body, i) {
						var colors = tooltipModel.labelColors[i];
						var style = "background:" + colors.backgroundColor;
						style += "; border-color:" + colors.borderColor;
						style += "; border-width: 2px";
						var span =
							'<span class="chartjs-tooltip-key" style="' +
							style +
							'"></span>';
						innerHtml += "<tr><td>" + span + body + "</td></tr>";
					});
					innerHtml += "</tbody>";

					var tableRoot = tooltipEl.querySelector("table");
					tableRoot.innerHTML = innerHtml;
				}

				// `this` 是整体的工具提示
				var position = this._chart.canvas.getBoundingClientRect();

				// 显示，位置和设置字体的样式
				tooltipEl.style.opacity = 1;
				tooltipEl.style.left =
					position.left + tooltipModel.caretX + "px";
				tooltipEl.style.top = position.top + tooltipModel.caretY + "px";
				tooltipEl.style.fontFamily = tooltipModel._fontFamily;
				tooltipEl.style.fontSize = tooltipModel.fontSize;
				tooltipEl.style.fontStyle = tooltipModel._fontStyle;
				tooltipEl.style.padding =
					tooltipModel.yPadding +
					"px " +
					tooltipModel.xPadding +
					"px";
			}
		}
	}
});
```

有关如何开始使用的示例，请参阅`samples/tooltips/line-customTooltips.html`。

## 提示框实体

提示框实体包含可用于呈现工具提示的参数。

```javascript
{
    // 在工具提示中呈现的项目。请参阅工具提示项目界面部分
    dataPoints: TooltipItem[],

    // 定位
    xPadding: Number,
    yPadding: Number,
    xAlign: String,
    yAlign: String,

    // X and Y properties are the top left of the tooltip
    x: Number,
    y: Number,
    width: Number,
    height: Number,
    // Where the tooltip points to
    caretX: Number,
    caretY: Number,

    // Body
    // The body lines that need to be rendered
    // Each pbject contains 3 parameters
    // before: String[] // lines of text before the line with the color square
    // lines: String[], // lines of text to render as the main item with color square
    // after: String[], // lines of text to render after the main lines
    body: Object[],
    // lines of text that appear after the title but before the body
    beforeBody: String[],
    // line of text that appear after the body and before the footer
    afterBody: String[],
    bodyFontColor: Color,
    _bodyFontFamily: String,
    _bodyFontStyle: String,
    _bodyAlign: String,
    bodyFontSize: Number,
    bodySpacing: Number,

    // Title
    // lines of text that form the title
    title: String[],
    titleFontColor: Color,
    _titleFontFamily: String,
    _titleFontStyle: String,
    titleFontSize: Number,
    _titleAlign: String,
    titleSpacing: Number,
    titleMarginBottom: Number,

    // Footer
    // lines of text that form the footer
    footer: String[],
    footerFontColor: Color,
    _footerFontFamily: String,
    _footerFontStyle: String,
    footerFontSize: Number,
    _footerAlign: String,
    footerSpacing: Number,
    footerMarginTop: Number,

    // Appearance
    caretSize: Number,
    cornerRadius: Number,
    backgroundColor: Color,

    // colors to render for each item in body[]. This is the color of the squares in the tooltip
    labelColors: Color[],

    // 0 opacity is a hidden tooltip
    opacity: Number,
    legendColorBackground: Color,
    displayColors: Boolean,
}
```
