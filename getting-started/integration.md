# 集成

Chart.js可以与JavaScript集成或与不同的模块加载器集成。 下面的例子显示了如何在不同的方式中加载Chart.js。

## ES6 Modules

```javascript
import Chart from 'chart.js'
var myChart = new Chart(ctx, {...})
```

## Script 标签

```html
<script src="path/to/Chartjs/dist/Chart.js"></script>
<script>
var myChart = new Chart(ctx, {...})
</script>
```

## Common JS

```javascript
var Chart = require('chart.js')
var myChart = new Chart(ctx, {...})
```

## Require JS

```javascript
require(['path/to/Chartjs/src/chartjs.js'], function(Chart){
    var myChart = new Chart(ctx, {...})
})
```