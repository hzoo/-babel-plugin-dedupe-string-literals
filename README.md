# babel-plugin-transform-dedupe-string-literals

Dedupe long strings in arrays as new variable declarations to save on disk space.

## Example

**In**

```js
['a', 'long string', 'long string'];
```

**Out**

```js
var _a = 'long string';
['a', _a, _a];
```

## Installation

```sh
# if babel isn't already installed, it creates a `babel` cli command
$ npm install babel-cli
$ npm install babel-plugin-transform-dedupe-string-literals
```

## Options

`minimumStringLength` - The minimum string length that will apply this transform. If the string length is too small, it will leave the string as is.

> This means that a string like `'a'` with a length of 1 won't get a new variable created for it.

## Usage

### Via `.babelrc` config file (Recommended)

**.babelrc**

```js
// without options
{
  "plugins": ["transform-dedupe-string-literals"]
}

// with options
{
  "plugins": [
    ["transform-dedupe-string-literals", {
      "minimumStringLength": 20 // defaults to 7
    }]
  ]
}
```

### Via CLI

```sh
$ babel --plugins transform-dedupe-string-literals script.js
```

### Via Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-dedupe-string-literals"]
});
```