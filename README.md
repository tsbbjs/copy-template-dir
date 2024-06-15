copy-template-dir
===

[![CI](https://github.com/tsbbjs/copy-template-dir/actions/workflows/ci.yml/badge.svg)](https://github.com/tsbbjs/copy-template-dir/actions/workflows/ci.yml)
[![npm version](https://img.shields.io/npm/v/@tsbb/copy-template-dir.svg)](https://www.npmjs.com/package/@tsbb/copy-template-dir)

High throughput template dir writes. Supports variable injection using the
mustache `{{ }}` syntax.

## Installation

```sh
$ npm install copy-template-dir
```

## Usage

```js
const copy = require('copy-template-dir')
const path = require('path')

const vars = { foo: 'bar' }
const inDir = path.join(process.cwd(), 'templates')
const outDir = path.join(process.cwd(), 'dist')

copy(inDir, outDir, vars, (err, createdFiles) => {
  if (err) throw err
  createdFiles.forEach(filePath => console.log(`Created ${filePath}`))
  console.log('done!')
})
```

## API

### copyTemplateDir(templateDir, targetDir, vars, cb)

Copy a directory of files over to the target directory, and inject the files
with variables. Takes the following arguments:
- __templateDir__: The directory that holds the templates. Filenames prepended
  with a `_` will have it removed when copying. Dotfiles need to be prepended
  with a `_`. Files and filenames are populated with variables using the
  `{{varName}}` syntax.
- __targetDir__: the output directory
- __vars__: An object with variables that are injected into the template files
  and file names.
- __cb(err, createdFiles)__: A callback that is called on completion, with
paths to created files if there were no errors.

## See Also
- [maxstache-stream](https://github.com/yoshuawuyts/maxstache-stream)

## License

[MIT](https://tldrlegal.com/license/mit-license)
