# ls-chunk-store [![travis][travis-image]][travis-url] [![npm][npm-image]][npm-url] [![downloads][downloads-image]][downloads-url]
                 
[travis-image]: https://img.shields.io/travis/DiegoRBaquero/ls-chunk-store.svg?style=flat
[travis-url]: https://travis-ci.org/DiegoRBaquero/ls-chunk-store
[npm-image]: https://img.shields.io/npm/v/ls-chunk-store.svg?style=flat
[npm-url]: https://npmjs.org/package/ls-chunk-store
[downloads-image]: https://img.shields.io/npm/dm/ls-chunk-store.svg?style=flat
[downloads-url]: https://npmjs.org/package/ls-chunk-store

#### Browser localStorage chunk store that is [abstract-chunk-store](https://github.com/mafintosh/abstract-chunk-store) compliant

[![abstract chunk store](https://cdn.rawgit.com/mafintosh/abstract-chunk-store/master/badge.svg)](https://github.com/mafintosh/abstract-chunk-store)

## Features

- Chunks that don't fit in localStorage remain in memory
- Works as a persistent cache of chunks
- Oldest ls-chunk-store chunks are removed when store is full

## Install

```
npm install ls-chunk-store
```

####You can also use the browserified version from jsDelivr:
````html
<script src="https://cdn.jsdelivr.net/ls-chunk-store/latest/ls-chunk-store.min.js"></script>
````
And simply use lsChunkStore from your app. ([Example](https://github.com/DiegoRBaquero/BTorrent/blob/ls-chunk-store/app.coffee#L6))


## Build

The following command will build ls-chunk-store.min.js in the dist folder
```
npm run-script build
```
The following command will build ls-chunk-store.js in the root folder
```
npm run-script build-dev
```

## Usage

### Generate random prefix

``` js
var LSChunkStore = require('ls-chunk-store')

var chunks = new LSChunkStore(10)
```

### Use specified prefix

``` js
var LSChunkStore = require('ls-chunk-store')

var chunks = new LSChunkStore(10, {
  prefix: 'myFile.txt'
})
```

### put, get, close, destroy

```js
chunks.put(0, new Buffer('0123456789'), function (err) {
  if (err) throw err

  chunks.get(0, function (err, chunk) {
    if (err) throw err
    console.log(chunk) // '0123456789' as a buffer

    chunks.close(function (err) {
      if (err) throw err
      console.log('storage is closed')

      chunks.destroy(function (err) {
        if (err) throw err
        console.log('files is deleted')
      })
    })
  })
})
```

## License

MIT. Copyright (c) [Diego Rodríguez Baquero](http://diegorbaquero.com).
