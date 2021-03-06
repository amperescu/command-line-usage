[![view on npm](http://img.shields.io/npm/v/command-line-usage.svg)](https://www.npmjs.org/package/command-line-usage)
[![npm module downloads](http://img.shields.io/npm/dt/command-line-usage.svg)](https://www.npmjs.org/package/command-line-usage)
[![Build Status](https://travis-ci.org/75lb/command-line-usage.svg?branch=master)](https://travis-ci.org/75lb/command-line-usage)
[![Dependency Status](https://badgen.net/david/dep/75lb/command-line-usage)](https://david-dm.org/75lb/command-line-usage)
[![Coverage Status](https://coveralls.io/repos/github/75lb/command-line-usage/badge.svg?branch=next)](https://coveralls.io/github/75lb/command-line-usage?branch=master)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/feross/standard)

***Upgraders, please check the [release notes](https://github.com/75lb/command-line-usage/releases).***

# command-line-usage

A simple, data-driven module for creating a usage guide.

## Synopsis

A usage guide is created by first defining an arbitrary number of sections, e.g. a description section, synopsis, option list, examples, footer etc. Each section has an optional header, some content and must be of type <code><a href="#commandlineusagecontent">content</a></code> or <code><a href="#commandlineusageoptionlist">optionList</a></code>. This section data is passed to <code><a href="#commandlineusagesections--string-">commandLineUsage()</a></code> which returns a usage guide.

Inline ansi formatting can be used anywhere within section content using [chalk template literal syntax](https://github.com/chalk/chalk#tagged-template-literal).

For example, this script:
```js
const commandLineUsage = require('command-line-usage')

const sections = [
  {
    header: 'A typical app',
    content: 'Generates something {italic very} important.'
  },
  {
    header: 'Options',
    optionList: [
      {
        name: 'input',
        typeLabel: '{underline file}',
        description: 'The input to process.'
      },
      {
        name: 'help',
        description: 'Print this usage guide.'
      }
    ]
  }
]
const usage = commandLineUsage(sections)
console.log(usage)
```

Outputs this guide:

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/synopsis.png" width="90%">

## Some examples

### Typical

A fairly typical usage guide with three sections - description, option list and footer. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-create-a-typical-usage-guide).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/simple.png" width="90%">

### Option List groups

Demonstrates breaking the option list up into groups. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-break-the-option-list-up-into-groups).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/groups.png" width="90%">

### Banners

A banner is created by adding the `raw: true` property to your `content`. This flag disables any formatting on the content, displaying it raw as supplied.

#### Header

Demonstrates a banner at the top. This example also adds a `synopsis` section. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-add-a-banner-to-your-usage-guide#code).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/header.png" width="90%">

#### Footer

Demonstrates a footer banner. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-add-a-banner-to-your-usage-guide#code-1).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/footer.png" width="90%">

### Examples section (table layout)

An examples section is added. To achieve this table layout, supply the `content` as an array of objects. The property names of each object are not important, so long as they are consistent throughout the array. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-add-an-examples-section-to-your-usage-guide).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/example-columns.png" width="90%">

### Advanced optionList layout

The `optionList` layout is fully configurable by setting the `tableOptions` property with an options object suitable for passing into [table-layout](https://github.com/75lb/table-layout#table-). This example overrides the default column widths and adds flame padding. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-use-advanced-optionList-table-formatting).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/option-list-options.png" width="90%">

### Command list

Useful if your app is command-driven, like git or npm. [Code](https://github.com/75lb/command-line-usage/wiki/How-to-add-a-command-list-to-your-usage-guide).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/command-list.png" width="90%">

### Description section (table layout)

Demonstrates supplying specific [table layout](https://github.com/75lb/table-layout) options to achieve more advanced layout. In this case the second column (containing the hammer and sickle) has a fixed `width` of 40 and `noWrap` enabled (as the input is already formatted as desired). [Code](https://github.com/75lb/command-line-usage/wiki/How-to-add-a-description-section-to-your-usage-guide).

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/description-columns.png" width="90%">

### Real-life

The [polymer-cli](https://github.com/Polymer/polymer-cli/) usage guide is a good real-life example.

<img src="https://raw.githubusercontent.com/75lb/command-line-usage/master/example/screens/polymer.png" width="90%">

## Documentation

* [API Reference](https://github.com/75lb/command-line-usage/blob/master/doc/api.md)
* [The full list of examples](https://github.com/75lb/command-line-usage/wiki)

* * *

&copy; 2015-19 Lloyd Brookes \<75pound@gmail.com\>. Documented by [jsdoc-to-markdown](https://github.com/75lb/jsdoc-to-markdown).
