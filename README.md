# if-env

> Simplify npm scripts with `if-env ... && npm run this || npm run that`

- - -

**For conditions that involve only the NODE_ENV parameter - I recommend switching to [`per-env`](https://github.com/ericclemmons/per-env), which is much simpler and much more powerful!**

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
  "start": "if-env NODE_ENV=production && npm run start:prod || npm run start:dev",
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
