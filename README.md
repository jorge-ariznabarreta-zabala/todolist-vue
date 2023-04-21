# todolist-vue
npm create vue@latest

cd todolist-vue
  npm install
  npm run format
  npm run dev

npm install --save-dev sass

npx json-server --watch db.json

## Bootstrap en VUE3
https://stackoverflow.com/questions/65547199/using-bootstrap-5-with-vue-3

Install bootstrap as you would any other JS module in the Vue project using npm install or by adding it to the package.json...

npm install --save bootstrap
npm install --save @popperjs/core

Next, add the Bootstrap CSS and JS components to the Vue project entrypoint (ie: src/main.js)...

import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"


## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
