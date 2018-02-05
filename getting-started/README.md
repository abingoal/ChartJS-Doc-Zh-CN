# 入门

老司机开车了

首先，需要在页面中创建一个`canvas`

```html
<canvas id="myChart"></canvas>
```

然后需要在页面中引用Chart.js

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.4.0/Chart.min.js" />
```
现在我们就可以创建一个图表了，在页面中添加以下脚本：

```javascript
var ctx = document.getElementById('myChart').getContext('2d');
var chart = new Chart(ctx, {
    // 要创建的图表类型
    type: 'line',

    // 数据集
    data: {
        labels: ["January", "February", "March", "April", "May", "June", "July"],
        datasets: [{
            label: "My First dataset",
            backgroundColor: 'rgb(255, 99, 132)',
            borderColor: 'rgb(255, 99, 132)',
            data: [0, 10, 5, 2, 20, 30, 45],
        }]
    },

    // 配置选项
    options: {}
});
```

是不是很容易！

接下来的文档可以帮助你使用缩放、工具提示、标签颜色、自定义操作等进行自定义图表。v

`Chart.js`的许多示例可以在`Chart.js.zip`的`/ samples`文件夹中提供，并附加到[每个版本](https://github.com/chartjs/Chart.js/releases)。