# ls-chunk-store [![travis][travis-image]][travis-url] [![npm][npm-image]][npm-url] [![downloads][downloads-image]][downloads-url]
                 
[travis-image]: https://img.shields.io/travis/DiegoRBaquero/ls-chunk-store.svg?style=flat
[travis-url]: https://travis-ci.org/DiegoRBaquero/ls-chunk-store
[npm-image]: https://img.shields.io/npm/v/ls-chunk-store.svg?style=flat
[npm-url]: https://npmjs.org/package/ls-chunk-store
[downloads-image]: https://img.shields.io/npm/dm/ls-chunk-store.svg?style=flat
[downloads-url]: https://npmjs.org/package/ls-chunk-store

#### Browser localStorage chunk store that is [abstract-chunk-store](https://github.com/mafintosh/abstract-chunk-store) compliant

## Install

```
npm install ls-chunk-store
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