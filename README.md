# actions-exec-wrapper

[@actions/exec](https://www.npmjs.com/package/@actions/exec) wrapper to get listener data value as return value.

## Usage
```js
const exec = require('actions-exec-wrapper');
// instead of
// const exec = require('@actions/exec');

const options = {};
options.cwd = './lib';
const { stdoutStr: myOutput, stderrStr: myError } = await exec.exec('node', ['index.js', 'foo=bar'], options);
```

### Using @actions/exec
```js
const exec = require('@actions/exec');

let myOutput = '';
let myError = '';

const options = {};
options.listeners = {
  stdout: (data: Buffer) => {
    myOutput += data.toString();
  },
  stderr: (data: Buffer) => {
    myError += data.toString();
  }
};
options.cwd = './lib';

await exec.exec('node', ['index.js', 'foo=bar'], options);
```
Above code from [actions/toolkit repository](https://github.com/actions/toolkit/tree/master/packages/exec)

## Install
```shell
$ npm install actions-exec-wrapper
$ # or
$ yarn add actions-exec-wrapper
```

## Description
- stdout
- stdoutStr
- stderr
- stderrStr
- stdline
- errline
- debug