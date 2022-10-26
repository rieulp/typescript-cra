# TypeScript CRA with husky

## 설치

```shell
npm install
```

## 실행

```shell
npm start
```

## husky script

- ### pre-commit
  commit 전에 prettier 적용
- ### pre-push
  git push전에 eslint 검사

## prettier 설정

```json
// .prettierrc
{
  "trailingComma": "none",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": false,
  "arrowParens": "always",
  "printWidth": 80
}
```

## eslint 설정

```json
// .eslintrc.json
{
  "env": {
    "browser": true,
    "es2021": true,
    "node": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "overrides": [],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["react", "@typescript-eslint"],
  "rules": {
    "no-var": "error",
    "no-multiple-empty-lines": "error",
    "no-console": ["error", { "allow": ["warn", "error", "info"] }],
    "eqeqeq": "error",
    "dot-notation": "warn",
    "no-unused-vars": "error",
    "quotes": ["error", "double"]
  }
}
```

## 절대경로 설정

### tsconfig.json

```json
"baseUrl": ".",
"paths": {
    "@/*": ["src/*"]
}
```

### config-overrides.js

```js
/* eslint-disable @typescript-eslint/no-var-requires */
const { addWebpackAlias, override } = require("customize-cra");
const path = require("path");

module.exports = override(
  addWebpackAlias({
    "@": path.resolve(__dirname, "src")
  })
);
```
