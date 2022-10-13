# vue-site

This template should help get you started developing with Vue 3 in Vite.

<h2>Recommended IDE Setup</h2>

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

<h2>Type Support for `.vue` Imports in TS</h2>

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
    1) Run `Extensions: Show Built-in Extensions` from VSCode's command palette
    2) Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

<h2>Customize configuration</h2>

See [Vite Configuration Reference](https://vitejs.dev/config/).

<h2>Project Setup</h2>

```sh
npm install
```

#<h2>Compile and Hot-Reload for Development</h2>

```sh
npm run dev
```

#<h2>Type-Check, Compile and Minify for Production</h2>

```sh
npm run build
```
