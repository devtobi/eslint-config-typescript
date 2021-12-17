# @vue/eslint-config-typescript

> eslint-config-typescript for vue-cli

See [@typescript-eslint/eslint-plugin](https://typescript-eslint.io/rules/) for available rules.

This config is specifically designed to be used by Vue CLI & `create-vue` setups
and is not meant for outside use (it can be used but some adaptations
on the user side might be needed - for details see the config file).

A part of its design is that this config may implicitly depend on
other parts of Vue CLI setups, such as `eslint-plugin-vue` being
extended in the same resulting config.

## Installation

In order to work around [a known limitation in ESLint](https://github.com/eslint/eslint/issues/3458), we recommend you to use this package alongside `@rushstack/eslint-patch`, so that you don't have to install too many dependencies:

```sh
npm install --dev @vue/eslint-config-typescript @rushstack/eslint-patch
```

## Usage

This package comes with 2 rulesets.

### `@vue/eslint-config-typescript`

This ruleset is the base configuration for Vue-TypeScript projects.
Besides setting the parser and plugin options, it also turns off several conflicting rules in the `eslint:recommended` ruleset.
So when used alongside other sharable configs, this config should be placed at the end of the `extends` array.

An example `.eslintrc.cjs`:

```js
require("@rushstack/eslint-patch/modern-module-resolution")

module.exports = {
  extends: [
    'plugin:vue/essential',
    'eslint:recommended',
    '@vue/eslint-config-typescript'
  ]
}
```

### `@vue/eslint-config-typescript/recommended`

This is extended from the `@typescript-eslint/recommended` ruleset, which is an **_opinionated_** ruleset.
See the [original documentation](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/src/configs#recommended) for more information.

Some of its rules, however, might conflict with `prettier`.
So when used alongside other sharable configs, this config should be placed after all other configs except for the one from `eslint-plugin-prettier` in the `extends` array.

An example `.eslintrc.cjs`:

```js
require("@rushstack/eslint-patch/modern-module-resolution")

module.exports = {
  extends: [
    'plugin:vue/essential',
    '@vue/eslint-config-typescript/recommended',

    'plugin:prettier/recommended'
  ]
}
```

### With Other Community Configs

If you are following the [`standard`](https://standardjs.com/) or [`airbnb`](https://github.com/airbnb/javascript/) style guides, don't manually extend from this package.
Please use `@vue/eslint-config-standard-typescript` or `@vue/eslint-config-airbnb-typescript` instead.
