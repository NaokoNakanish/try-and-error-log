# Reference
https://prettier.io/docs/en/install.html
https://eslint.org/docs/user-guide/command-line-interface
よくわからんのだが・・・

## eslint
```
npm i -g eslint

✔ How would you like to use ESLint? · style
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · vue
✔ Does your project use TypeScript? · No  
✔ Where does your code run? · browser               
✔ How would you like to define a style for your project? · guide
✔ Which style guide do you want to follow? · standard
✔ What format do you want your config file to be in? · JavaScript

Checking peerDependencies of eslint-config-standard@latest
The config that you've selected requires the following dependencies:

eslint-plugin-vue@latest eslint-config-standard@latest eslint@^7.12.1 eslint-plugin-import@^2.22.1 eslint-plugin-node@^11.1.0 eslint-plugin-promise@^4.2.1 || ^5.0.0
✔ Would you like to install them now with npm? ·Yes
......
successfully created .eslintrc.js file in /Users/nn/nm-recipes-mobile
```
こんなかんじでポチポチやっていった
`.eslintrc.js`というファイルができる、デフォルトのままで触らなくてもとりあえず動きそう


## pritter

```
npm install --save-dev --save-exact prettier
```

@`prettierrc.js` <--`prettierrc.json`でファイル出来てるけど、`.js`に変えた
もともと空っぽなのだが、以下だけ追加
```
module.exports = {
  singleQuote: true,
  semi: false,
}
```

## setting.json
以下に置き換える
```
{
  "vetur.validation.template": false, <!-- veturのほうをfalseにしないといけないらしい -->
  "eslint.validate": [
    {
      "language": "vue",
      "autoFix": true
    },
    {
      "language": "html",
      "autoFix": true
    },
    {
      "language": "javascript",
      "autoFix": true
    }
  ],
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.workingDirectories": ["./client", "./server"]
}
```
参考：https://www.vuemastery.com/courses/real-world-vue-js/optimizing-your-editor

## package.jsonの"devDependencies"はこんなかんじになる
```
"devDependencies": {
    "@nativescript/android": "8.0.0",
    "@nativescript/ios": "^8.0.0",
    "@nativescript/webpack": "beta",
    "eslint": "^7.30.0",
    + "eslint-config-standard": "^16.0.3",
    + "eslint-plugin-import": "^2.23.4",
    + "eslint-plugin-node": "^11.1.0",
    + "eslint-plugin-promise": "^5.1.0",
    + "eslint-plugin-vue": "^7.13.0",
    "nativescript-vue-template-compiler": "~2.9.0",
    + "prettier": "2.3.2",
    "sass": "^1.32.8"
  },
```
## .eslintrc.js
```
module.exports = {
  root: true,
  env: {
    node: true,
  },
  extends: ['plugin:vue/essential', 'eslint:recommended', '@vue/prettier'],
  rules: {
    'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
  },
  parserOptions: {
    parser: 'babel-eslint',
  },
}

```
