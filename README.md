# Chart.js

[![Chart.js on Slack](https://img.shields.io/badge/slack-Chart.js-blue.svg)](https://chart-js-automation.herokuapp.com/)

## 安装

从[GitHub releases](https://github.com/chartjs/Chart.js/releases/latest)下载Chart.js的最新版本 或者使用 [Chart.js CDN](https://cdnjs.com/libraries/Chart.js)。
 详细的安装说明可以在此[安装页面](./getting-started/installation.md)查看。

## 创建一个图表

Chart.js很容易上手，只需要在页面中引用脚本文件，并创建`<canvas>`节点即可渲染出图表。

下面的例子创建了一个单数据集的Bar图表。完整的文档可查看[使用文档](./getting-started/usage.md)
```html
<canvas id="myChart" width="400" height="400"></canvas>
<script>
var ctx = document.getElementById("myChart").getContext('2d');
var myChart = new Chart(ctx, {
    type: 'bar',
    data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [{
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
                'rgba(255,99,132,1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero:true
                }
            }]
        }
    }
});
</script>
```

## 贡献

在提交issue和pull request之前请先详细阅读[contributing guidelines](https://github.com/chartjs/Chart.js/blob/master/docs/developers/contributing.md)。

对于使用Chart.js的支持，请在[Stack Overflow](http://stackoverflow.com/questions/tagged/chartjs)上使用`chartjs`标签发布问题。

## 许可

Chart.js is available under the [MIT license](http://opensource.org/licenses/MIT).
