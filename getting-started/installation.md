# 安装
Chart.js 可以通过`npm`或`bower`这两种方式安装。

## npm

```bash
npm install chart.js --savev
```

## Bower

```bash
bower install chart.js --save
```

## CDN
或者使用[Chart.js CDN](https://cdnjs.com/libraries/Chart.js)


## Github
你也可以从这里[Chart.js on GitHub](https://github.com/chartjs/Chart.js/releases/latest)下载最新的发布版。

如果你download或clone了该项目，务必要先[构建 Chart.js](../developers/contributing.md#building-chartjs)以生成`dist`文件。Chart.js不再附带发布版，因此强烈建议下载发布版本。

# 选择合适的构建方式

Chart.js 提供了两种不同的构建方式供你选择。

## 独立构建
文件:
* `dist/Chart.js`
* `dist/Chart.min.js`

此版本仅包含Chart.js。如果使用此版本，并且需要时间轴，则需要在构建之前将[Moment.js](http://momentjs.com/)包含进项目。


## 完整构建
文件:
* `dist/Chart.bundle.js`
* `dist/Chart.bundle.min.js`

此版本包含了`Moment.js`。如果你想使用时间轴并希望包含单个文件，则应该使用该版本。如果你已经在应用程序中引用了Moment.js，请使用上面的构建方式，不然将会在程序中包含两个Moment.js，这样会导致页面加载时间增加或潜在的版本引用问题。