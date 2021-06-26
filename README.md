# svelte-horizontal-scroller

A pretty strightforward, simple, and unstyled Horizontal Scroller for Svelte.

Support for mobile, and dekstop drag & drop.


## Demo

[https://svelte.dev/repl/d37e9362f2284ea0a5bcd7011005ee19?version=3.38.3](https://svelte.dev/repl/d37e9362f2284ea0a5bcd7011005ee19?version=3.38.3)

Your package.json has a `"svelte"` field pointing to `src/index.js`, which allows Svelte apps to import the source code directly, if they are using a bundler plugin like [rollup-plugin-svelte](https://github.com/sveltejs/rollup-plugin-svelte) or [svelte-loader](https://github.com/sveltejs/svelte-loader) (where [`resolve.mainFields`](https://webpack.js.org/configuration/resolve/#resolve-mainfields) in your webpack config includes `"svelte"`). **This is recommended.**

For everyone else, `npm run build` will bundle your component's source code into a plain JavaScript module (`dist/index.mjs`) and a UMD script (`dist/index.js`). This will happen automatically when you publish your component to npm, courtesy of the `prepublishOnly` hook in package.json.
