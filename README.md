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

## How to deploy VUE app in github pages
https://learnvue.co/articles/deploy-vue-to-github-pages
Step 1. Set publicPath in vue.config.js to our repository name

On the master branch, we want to create a vue.config.js file in the root directory of our project. Here, we want to configure the publicPath (which also edits the webpack publicPath) to route all static assets to the proper path.

If we don’t have this configuration, our deployed site will not properly load assets such as images.

We want to route it to the URL path of our deployed GitHub Pages site, which we can find in our repository settings.

We want to take the path found in that red box – anything after github.io – and use it in our vue.config.jslike this.
vue.config.js

module.exports = {
  publicPath: process.env.NODE_ENV === "production" ? "/REPO_NAME/" : "/",
};
Change "/REPO_NAME/" for "/todolist-vue/", the name of your repo in github
Now, when we deploy our site, all the static assets should be loaded from the correct paths.

Step 2. Build your project using npm build

This step is pretty self explanatory, we actually need to have a dist folder to deploy.
Step 3. Run git add dist && git commit -m 'adding dist subtree'

This commits our changes to the master branch so that we can create a dist subtree in the next step. Make sure that dist is not included in your .gitignorefile!
Step 4. Run git subtree push --prefix dist origin gh-pages

This step makes gh-pages a subtree of our master branch. The prefix option specifies the folder that we want for our the subtree. If we take a look at our gh-pages branch, we will see that it is equivalent to being the root of the dist folder.

Step 5. Done

In a few minutes, GitHub Pages should refresh with your newest repository changes, and you should be able to see your Vue project online. Exciting!
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
