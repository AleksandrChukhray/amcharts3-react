How to install
==============

1. Create a `package.json` which includes `react`, `react-dom`, and `@amcharts/amcharts3-react`:

   ```json
   {
     "devDependencies": {
       "react": "^15.4.2",
       "react-dom": "^15.4.2",
       "@amcharts/amcharts3-react": "^2.0.0"
     }
   }
   ```

2. Run `npm install`

3. Use `<script>` tags in your HTML file to load AmCharts:

   ```html
   <script src="https://www.amcharts.com/lib/3/amcharts.js"></script>
   <script src="https://www.amcharts.com/lib/3/serial.js"></script>
   <script src="https://www.amcharts.com/lib/3/themes/light.js"></script>
   ```

4. If you are using `<script>` tags, include the `amcharts3-react.js` file in your HTML:

   ```html
   <script src="node_modules/@amcharts/amcharts3-react/amcharts3-react.js"></script>
   ```

   ----

   If you are using a bundler (like [Webpack](https://webpack.js.org/)), import the `@amcharts/amcharts3-react` plugin:

   ```js
   var AmCharts = require("@amcharts/amcharts3-react");
   ```

How to use
==========

```js
React.createElement(AmCharts.React, {
  "type": "serial",
  "theme": "light",
  "graphs": [...],
  "dataProvider": [...]
})
```

Or alternatively if you are using JSX:

```js
<AmCharts.React
  type="serial"
  theme="light"
  graphs={[...]}
  dataProvider={[...]} />
```

The configuration is exactly the same as the [`AmCharts.makeChart`](https://docs.amcharts.com/3/javascriptcharts/AmCharts#makeChart) method.

Changes to the configuration are automatically detected when rendering (you do not need to call [`validateNow`](https://docs.amcharts.com/3/javascriptcharts/AmSerialChart#validateNow) or [`validateData`](https://docs.amcharts.com/3/javascriptcharts/AmSerialChart#validateData)).

In addition, this plugin automatically generates an `id`, so you do not need to specify it.

----

If you want to use plugins (like [dataloader](https://github.com/amcharts/dataloader), [export](https://github.com/amcharts/export), [responsive](https://github.com/amcharts/responsive), [animate](https://github.com/amcharts/animate), etc.) you will need to include the appropriate `<script>` tags.

Here is an example for the [export](https://github.com/amcharts/export) plugin:

```html
<link rel="stylesheet" href="https://www.amcharts.com/lib/3/plugins/export/export.css" type="text/css" media="all" />

<script src="https://www.amcharts.com/lib/3/plugins/export/export.min.js"></script>
```

You can see an example program in the `examples/webpack-export` folder. It updates the chart's `dataProvider` every 3 seconds.


## Changelog

### 2.0.0
* Major breaking change: this plugin no longer automatically imports AmCharts, so you must use `<script>` tags to load AmCharts

* Major breaking change: you must now use `AmCharts.React` rather than `AmCharts`

### 1.1.8
* Fixing another bug with updating the chart data

### 1.1.7
* Fixing a bug where the chart does not zoom out when changing the `dataProvider`

### 1.1.6
* Fixing a bug where the chart won't show up properly on the first update

### 1.1.5
* Fixing a bug which caused stock charts to not update correctly

### 1.1.4
* Deprecating using `AmCharts` with Webpack, instead use `AmCharts.React`
* Adding in the various global `AmCharts` properties for Webpack

### 1.1.3
* Fixing a bug that caused the `listeners` to trigger multiple times

### 1.1.2
* Fixing an [issue when using `amcharts3-react` on the server](https://github.com/amcharts/amcharts3-react/issues/11)

### 1.1.1
* Fixing an [issue with `peerDependencies`](https://github.com/npm/npm/issues/3218)

### 1.1.0
* Adding in support for npm / Webpack

### 1.0.0
* Initial release
