#From shell output to json

Converts the usual, space separated, table from a shell command into a list of json object where the keys are the columns' names and the values the different data for each row.

### Install

You can install this library through [NPM](https://www.npmjs.org/package/node-shell-parser):

```bash
npm install -g node-shell-parser
```

### Definition:

```javascript
  shellParser(shellOutput, options);
```

* shellOutput: the string resulting from running your command
* options.separator: which character separates your tabled data, default is one space.
* options.skipLines: how many lines to skip before meeting the columns definition header

### Usage

```javascript

var shellParser = require('node-shell-parser');
var child = require('child_process');

var process = child.spawn('ps');
var shellOutput = '';

process.stdout.on('data', function (chunk) {
  shellOutput += chunk;
});

process.stdout.on('end', function () {
  console.log(shellParser(shellOutput))
});
```