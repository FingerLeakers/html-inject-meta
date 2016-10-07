# metadataify

> Stream meta tags into html

[![experimental][stability-experimental]][stability-url]
<!--[![Build Status][travis-image]][travis-url]-->
<!--[![npm version][npm-image]][npm-url]-->
<!--[![Dependency Status][david-dm-image]][david-dm-url]-->
<!--[![Semistandard Style][semistandard-image]][semistandard-url]-->


## Introduction

See: [indexhtmlify#5](https://github.com/dominictarr/indexhtmlify/issues/5)

## Example

*Not yet published to npm*. When published,

```
$ npm i -g metadataify 
```

To use:

```bash
$ cat index.html | metadataify
```

Or even better:

```bash
$ browserify index.js | indexhtmlify | metadataify > index.html
```

`metadataify` is designed to just work without much configuration, but also to allow increasingly precise overrides when necessary. Used without any arguments, it looks for the nearest `package.json` and uses the following rules (in _increasing_ order of precedence) to determine the metadata:

1. from input data (default = nearest `package.json`) using basic rules (e.g. `description` -> `twitter:description`)
2. from `metadataify` field of input data using same basic rules as 1.
3. from `metadataify` field of input data using specific rules (e.g. `{metadataify: {twitter: {title: "..."}}`)
4. from command line override flags (e.g. `--title="...". Works for `title`, `description`, `author`, and `url`)

Applying this to a minimal html file using the `package.json` for this repo yields:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>metadataify</title>
    <meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" name="viewport" />
    <meta charset=utf-8><meta name="application-name" content="metadataify">
    <meta name="subject" content="Stream meta tags into html">
    <meta name="abstract" content="Stream meta tags into html">
    <meta name="twitter:title" content="metadataify">
    <meta name="description" content="Stream meta tags into html">
    <meta name="twitter:description" content="Stream meta tags into html">
    <meta name="author" content="Ricky Reusser">
    ...
  </head>
  <body></body>
</html>
```

_Note that this script *only* works on valid html files, which means that a `<title>` element must exist for the value to be set, and a `<head>` tag must exist for meta tags to be appended._

## See also

This module is heaviliy inspired by and may be used effectively with [indexhtmlify](https://github.com/dominictarr/indexhtmlify).

## License

&copy; 2016 Ricky Reusser. MIT License.

<!-- BADGES -->

[travis-image]: https://travis-ci.org/rreusser/metadataify.svg?branch=master
[travis-url]: https://travis-ci.org//metadataify

[npm-image]: https://badge.fury.io/js/metadataify.svg
[npm-url]: https://npmjs.org/package/metadataify

[david-dm-image]: https://david-dm.org/rreusser/metadataify.svg?theme=shields.io
[david-dm-url]: https://david-dm.org/rreusser/metadataify

[semistandard-image]: https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square
[semistandard-url]: https://github.com/Flet/semistandard

<!-- see stability badges at: https://github.com/badges/stability-badges -->
[stability-url]: https://github.com/badges/stability-badges
[stability-deprecated]: http://badges.github.io/stability-badges/dist/deprecated.svg
[stability-experimental]: http://badges.github.io/stability-badges/dist/experimental.svg
[stability-unstable]: http://badges.github.io/stability-badges/dist/unstable.svg
[stability-stable]: http://badges.github.io/stability-badges/dist/stable.svg
[stability-frozen]: http://badges.github.io/stability-badges/dist/frozen.svg
[stability-locked]: http://badges.github.io/stability-badges/dist/locked.svg
