Assets Transform extension for the HTML Webpack Plugin
========================================

[![License](https://img.shields.io/github/license/renofi/html-webpack-transform-plugin)](https://github.com/RenoFi/html-webpack-transform-plugin/blob/master/LICENSE)
[![npm](https://img.shields.io/npm/v/html-webpack-transform-plugin)](https://www.npmjs.com/package/html-webpack-transform-plugin)
[![Build Status](https://travis-ci.org/RenoFi/html-webpack-transform-plugin.svg?branch=master)](https://travis-ci.org/RenoFi/html-webpack-transform-plugin)

## About

This plugin will allow you to transform asset tags generated by [html-webpack-plugin](https://github.com/jantimon/html-webpack-plugin/).

## Installation

Install the plugin with npm:

```
npm i --save-dev html-webpack-transform-plugin
```

Install the plugin with yarn:

```
yarn add --dev html-webpack-transform-plugin
```

## Basic Usage

In the plugins section of your webpack config file, include the following:

```
new HtmlWebpackPlugin()
new HtmlWebpackTransformPlugin()
```

## Options
|Name|Type|Default|Description|
|:--:|:--:|:-----:|:----------|
|**`attributes`**|`{Object}`|`{}`|Map of attributes to add|
|**`pathPrefix`**|`{String}`|`''`|Path prefix to use with each asset url|
|**`transform`**|`{Function}`|`tag => tag`|A callback function that is execute on each tag to allow any transformation of tags. Function must return modified tag object|
|**`replacePublicPath`**|`{Boolean}`|`false`|Used with `pathPrefix` option. If true - `publicPath` from webpack options will be replaced with `pathPrefix`|

## Examples

Add `crossorigin` attribue for each script tag:
```
new HtmlWebpackTransformPlugin({
  attributes: {script: {crossorigin: 'anonymous'}},
}),
```

Replace public path with `ejs` template variable for dynamic paths with `expresjs`:
```
new HtmlWebpackTransformPlugin({
  pathPrefix: '<%= assetsPath %>/',
  replacePublicPath: true,
}),
```

Do anything else with the tags using `transform` callback:
```
new HtmlWebpackTransformPlugin({
  transform: tag => {
    // add additional properties
    // add path prefix or remove public path
    // or anything else
    return tag;
  },
}),
```
