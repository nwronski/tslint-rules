# nwronski-tslint-rules

This repo contains my TSLint rule configurations for projects that use
TypeScript and/or Angular.

## Installation

Use the [TypeScript Rules Installation](#typeScript-rules-installation) for
plain Node + TypeScript projects or the
[Angular Rules Installation](#angular-rules-installation) for
Angular + TypeScript projects.

### TypeScript Rules Installation

Install the `nwronski-tslint-rules` and `tslint` modules.

```shell
npm i -D nwronski-tslint-rules tslint
```

Create a `tslint.json` file in the root folder of your project and add
the following:

```json
{
  "extends": "nwronski-tslint-rules"
}
```

### Angular Rules Installation

Install the `nwronski-tslint-rules`, `tslint`, and `codelyzer` modules.

```shell
npm i -D nwronski-tslint-rules tslint codelyzer
```

Create a `tslint.json` file in the root folder of your project and add
the following:

```json
{
  "extends": "nwronski-tslint-rules/tslint-ng2.json",
  "rules": {
    "directive-selector": [ true, "attribute", "nw", "camelCase" ],
    "component-selector": [ true, "element", "nw", "kebab-case" ]
  }
}
```

Don't forget to change `nw` to your preferred prefix for component and directive
selectors.

## Usage

Add a script to the `scripts` section of your `package.json`, making sure to
set the correct pattern for your source files (the example uses `src/**/*.ts`):

```json
{
  "scripts": {
    "lint": "tslint --fix --config ./tslint.json --project ./tsconfig.json 'src/**/*.ts'"
  }
}
```

If you have a build script then you should modify it so that the linting is
done before the project can be successfully built. For example, you could
prepend the linting command to your build command to make sure the linting
is run first.

```shell
npm run lint
```
