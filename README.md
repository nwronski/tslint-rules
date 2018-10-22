# nwronski-tslint-rules

This repo contains the TSLint rule configuration for my projects that
use TypeScript as well as Angular 2 TypeScript projects.

## Installation

The instructions differ for plain TypeScript projects and for Angular 2 +
TypeScript projects, so follow the instructions that apply to your
project type.

### Basic Installation

Install TSLint and TypeScript for your project.

```
npm i -D typescript tslint
```

Install the `nwronski-tslint-rules` module.

```
npm i -D nwronski-tslint-rules
```

Create a `tslint.json` file in the root folder of your project and add
the following:

```json
{
  "rulesDirectory": [
    "node_modules/tslint-eslint-rules/dist/rules"
  ],
  "extends": "nwronski-tslint-rules/tslint-base"
}
```

### Angular 2 Installation

Install TSLint, Codelyzer and TypeScript for your project.

```
npm i -D typescript tslint codelyzer
```

Install the `nwronski-tslint-rules` module.

```
npm i -D nwronski-tslint-rules
```

Create a `tslint.json` file in the root folder of your project and add
the following:

```json
{
  "rulesDirectory": [
    "node_modules/codelyzer",
    "node_modules/tslint-eslint-rules/dist/rules"
  ],
  "extends": "nwronski-tslint-rules/tslint-ng2"
}
```

## Usage

Add a script to the `scripts` section of your `package.json`, making sure to
set the correct pattern for your source files (the example uses `src/**/*.ts`):

```json
{
  "scripts": {
    "lint": "tslint --fix --format codeFrame --project ./tsconfig.json 'src/**/*.ts'"
  }
}
```

If you have a build script then you should modify it so that the linting is
done before the project can be successfully built. For example, you could
prepend the linting command to your build command to make sure the linting
is run first.

```
npm run lint
```

### Recommended TypeScript compiler options

The TSLint configuration in this module pair well with the following
`compilerOptions` added to your `tsconfig.json` as an extra layer of
best practice enforcement:

```json
{
  "compilerOptions": {
    "strict": true,
    "noUnusedLocals": true,
    "allowUnreachableCode": false,
    "allowUnusedLabels": false,
    "forceConsistentCasingInFileNames": true,
    "noImplicitReturns": true,
    "noImplicitThis": true
  }
}
```
