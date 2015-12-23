# if-env

> Simplify npm scripts with `if-env ... && npm run this || npm run that`

[![travis build](https://img.shields.io/travis/if-env.svg?style=flat-square)](https://travis-ci.org/if-env)
[![Coverage Status](https://coveralls.io/repos/ericclemmons/if-env/badge.svg?branch=master&service=github&style=flat-square)](https://coveralls.io/github/ericclemmons/if-env?branch=master)
[![version](https://img.shields.io/npm/v/start-cluster.svg?style=flat-square)](http://npm.im/start-cluster)
[![downloads](https://img.shields.io/npm/dm/if-env.svg?style=flat-square)](http://npm-stat.com/charts.html?package=start-cluster)
[![MIT License](https://img.shields.io/npm/l/if-env.svg?style=flat-square)](http://opensource.org/licenses/MIT)

- - -

Suppose you want to simplify development and be able to run `npm start`
in all environments & run the correct scripts.

Your `package.json` might look like this:

```json
"scripts": {
  "start": "if [[ ${NODE_ENV} == \"production\" ]]; then npm run start:prod; else npm run start:dev; fi",
  "start:dev": "webpack",
  "start:prod": "start-cluster"
}
```

The problem is, this doesn't work in all environments.

Instead, you can write:

```json
"scripts": {
  "start": "if-env NODE_ENV=production && npm run start:prod || npm start:dev",
  "start:dev": "webpack",
  "start:prod": "start-cluster"
}
```


## Usage

### 1. Install

```shell
$ npm install if-env --save
```

### 2. Add to `package.json`

```json
"scripts": {
  "start": "if-env SOME_ENV_VAR=some_val ANOTHER_ENV_VAR=another_val && npm run this || npm run that"
}
```


## License

> MIT &copy; Eric Clemmons 2015
