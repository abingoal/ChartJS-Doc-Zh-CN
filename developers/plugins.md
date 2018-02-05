# 插件(Plugins)

插件是自定义或更改图表默认行为的最有效方式。它们已经在[2.1.0 版本](https://github.com/chartjs/Chart.js/releases/tag/2.1.0)（仅限于全局插件）中引入，并且在[2.5.0 版本](https://github.com/chartjs/Chart.js/releases/tag/2.5.0)（每个图表插件和选项）中进行了扩展。

## 使用插件

插件可以在图表实例之间共享：

```javascript
var plugin = {
	/* plugin implementation */
};

// chart1 and chart2 use "plugin"
var chart1 = new Chart(ctx, {
	plugins: [plugin]
});

var chart2 = new Chart(ctx, {
	plugins: [plugin]
});

// chart3 doesn't use "plugin"
var chart3 = new Chart(ctx, {});
```

插件也可以直接在图表插件配置（即*内联插件*）中定义：

```javascript
var chart = new Chart(ctx, {
	plugins: [
		{
			beforeInit: function(chart, options) {
				//..
			}
		}
	]
});
```

但是，当需要自定义选项适用于多个图表时，这种方法并不理想。

## 全局插件

插件可以在全局范围内注册，应用于所有图表（即*全局插件*）：

```javascript
Chart.plugins.register({
	// plugin implementation
});
```

> 注意: _inline_ 插件不能全局注册

## 配置

### 插件 ID

插件必须定义一个唯一的 ID 以便可配置。

该 id 应该遵循[npm 包名称约定](https://docs.npmjs.com/files/package.json#name)：

* 不能以点或下划线开头
* 不能包含任何非网址安全的字符
* 不能包含大写字母
* 简短并合理的描述

如果打算公开发布一个插件，你可能要检查[registry](https://www.npmjs.com/search?q=chartjs-plugin-)，看看该名字的插件是否已经存在。需要注意的是，在这种情况下，包名称应以 `chartjs-plugin-`为前缀，以显示在 Chart.js 插件注册表中。

### 插件选项

插件选项位于`options.plugins`配置下，并由插件 ID：`options.plugins.{plugin-id}`作为作用域。

```javascript
var chart = new Chart(ctx, {
    config: {
        foo: { ... },           // chart 'foo' option
        plugins: {
            p1: {
                foo: { ... },   // p1 plugin 'foo' option
                bar: { ... }
            },
            p2: {
                foo: { ... },   // p2 plugin 'foo' option
                bla: { ... }
            }
        }
    }
});
```

#### 禁用插件

要为特定图表禁用全局插件，插件选项必须设置为`false`：

```javascript
Chart.plugins.register({
	id: "p1"
	// ...
});

var chart = new Chart(ctx, {
	config: {
		plugins: {
			p1: false // disable plugin 'p1' for this instance
		}
	}
});
```

## 插件核心 API

可用钩子 (从 2.5 版本开始):

* beforeInit
* afterInit
* beforeUpdate _(cancellable)_
* afterUpdate
* beforeLayout _(cancellable)_
* afterLayout
* beforeDatasetsUpdate _(cancellable)_
* afterDatasetsUpdate
* beforeRender _(cancellable)_
* afterRender
* beforeDraw _(cancellable)_
* afterDraw
* beforeDatasetsDraw _(cancellable)_
* afterDatasetsDraw
* beforeEvent _(cancellable)_
* afterEvent
* resize
* destroy
