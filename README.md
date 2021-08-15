# SvelteKit build fail with adapter-static

When I specify `config.kit.paths.base`, I can't build.

## next150

Build fail and "Not Found" when preview

### How did I make

```
❯ npm init svelte@next next150

create-svelte version 2.0.0-next.78

Welcome to SvelteKit!

This is beta software; expect bugs and missing features.

If you encounter a problem, open an issue on https://github.com/sveltejs/kit/issues if none exists already.

✔ Which Svelte app template? › Skeleton project
✔ Use TypeScript? … No / Yes
✔ Add ESLint for code linting? … No / Yes
✔ Add Prettier for code formatting? … No / Yes
✔ Copied project files

Want to add other parts to your code base? Visit https://github.com/svelte-add/svelte-adders, a community project of commands to add particular functionality to Svelte projects


Next steps:
  1: cd next150
  2: npm install (or pnpm install, etc)
  3: git init && git add -A && git commit -m "Initial commit" (optional step)
  4: npm run dev -- --open

To close the dev server, hit Ctrl-C

Stuck? Visit us at https://svelte.dev/chat
```

I modified `package.json` and `svelte.config.js`.

*package.json*

```json
  "devDependencies": {
    "@sveltejs/adapter-static": "1.0.0-next.16",
    "@sveltejs/kit": "1.0.0-next.146",
    "svelte": "^3.34.0"
  },
```

*svelte.config.js*

```js
import adapt from '@sveltejs/adapter-static';
/** @type {import('@sveltejs/kit').Config} */
const config = {
	kit: {
		// hydrate the <div id="svelte"> element in src/app.html
		target: '#svelte',
		adapter: adapt(),
		paths: {
			base: '/base',
		},
	},
};

export default config;
```

Run `npm i` and `npm run build`

```
❯ npm i

added 30 packages, and audited 31 packages in 5s

4 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

❯ npm run build

> ~TODO~@0.0.1 build
> svelte-kit build

vite v2.4.4 building for production...
✓ 14 modules transformed.
.svelte-kit/output/client/_app/manifest.json                    1.21kb
.svelte-kit/output/client/_app/layout.svelte-96cb8070.js        0.53kb / brotli: 0.31kb
.svelte-kit/output/client/_app/pages/index.svelte-9d541552.js   0.80kb / brotli: 0.41kb
.svelte-kit/output/client/_app/assets/start-a8cd1609.css        0.16kb / brotli: 0.10kb
.svelte-kit/output/client/_app/error.svelte-9244150a.js         1.55kb / brotli: 0.64kb
.svelte-kit/output/client/_app/chunks/vendor-52401ce2.js        7.02kb / brotli: 2.62kb
.svelte-kit/output/client/_app/start-829fbcbd.js                17.65kb / brotli: 5.63kb
vite v2.4.4 building SSR bundle for production...
✓ 11 modules transformed.
.svelte-kit/output/server/app.js   11.23kb

Run npm run preview to preview your production build locally.

> Using @sveltejs/adapter-static
> 404 /_app/start-829fbcbd.js (linked from /)
Error: 404 /_app/start-829fbcbd.js (linked from /)
    at file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:84:11
    at visit (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:207:5)
    at async visit (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:275:6)
    at async prerender (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:285:6)
    at async Object.prerender (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:346:4)
    at async adapt (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/adapter-static/index.js:17:4)
    at async adapt (file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/chunks/index6.js:371:2)
    at async file:///Users/sotaro/Dev/trainings/sveltekit-static-build-fail/next150/node_modules/@sveltejs/kit/dist/cli.js:913:5
```

Additional info

```
❯ npx envinfo --system --binaries --browsers --npmPackages "{svelte,@sveltejs/*,vite}"

  System:
    OS: macOS 11.5.1
    CPU: (8) x64 Apple M1
    Memory: 28.92 MB / 16.00 GB
    Shell: 5.8 - /bin/zsh
  Binaries:
    Node: 14.17.4 - /usr/local/bin/node
    Yarn: 1.22.10 - /usr/local/bin/yarn
    npm: 7.20.5 - /usr/local/bin/npm
  Browsers:
    Chrome: 92.0.4515.131
    Firefox: 91.0
    Safari: 14.1.2
  npmPackages:
    @sveltejs/adapter-static: 1.0.0-next.16 => 1.0.0-next.16
    @sveltejs/kit: 1.0.0-next.146 => 1.0.0-next.146
    svelte: ^3.34.0 => 3.42.1
```

## next146

No Problem!!

### How did I make

```
❯ npm init svelte@next next146

create-svelte version 2.0.0-next.78

Welcome to SvelteKit!

This is beta software; expect bugs and missing features.

If you encounter a problem, open an issue on https://github.com/sveltejs/kit/issues if none exists already.

✔ Which Svelte app template? › Skeleton project
✔ Use TypeScript? … *No* / Yes
✔ Add ESLint for code linting? … *No* / Yes
✔ Add Prettier for code formatting? … *No* / Yes
✔ Copied project files

Want to add other parts to your code base? Visit https://github.com/svelte-add/svelte-adders, a community project of commands to add particular functionality to Svelte projects


Next steps:
  1: cd next146
  2: npm install (or pnpm install, etc)
  3: git init && git add -A && git commit -m "Initial commit" (optional step)
  4: npm run dev -- --open

To close the dev server, hit Ctrl-C

Stuck? Visit us at https://svelte.dev/chat
```

I modified `package.json` and `svelte.config.js`.

*package.json*

```json
  "devDependencies": {
    "@sveltejs/adapter-static": "1.0.0-next.16",
    "@sveltejs/kit": "1.0.0-next.146",
    "svelte": "^3.34.0"
  },
```

*svelte.config.js*

```js
import adapt from '@sveltejs/adapter-static';
/** @type {import('@sveltejs/kit').Config} */
const config = {
	kit: {
		// hydrate the <div id="svelte"> element in src/app.html
		target: '#svelte',
		adapter: adapt(),
		paths: {
			base: '/base',
		},
	},
};

export default config;
```

Run `npm i` and `npm run build`

```
❯ npm i

added 30 packages, and audited 31 packages in 6s

4 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

❯ npm run build

> ~TODO~@0.0.1 build
> svelte-kit build

vite v2.4.4 building for production...
✓ 14 modules transformed.
.svelte-kit/output/client/_app/manifest.json                    1.21kb
.svelte-kit/output/client/_app/layout.svelte-96cb8070.js        0.53kb / brotli: 0.31kb
.svelte-kit/output/client/_app/pages/index.svelte-9d541552.js   0.80kb / brotli: 0.41kb
.svelte-kit/output/client/_app/error.svelte-9244150a.js         1.55kb / brotli: 0.64kb
.svelte-kit/output/client/_app/assets/start-a8cd1609.css        0.16kb / brotli: 0.10kb
.svelte-kit/output/client/_app/chunks/vendor-52401ce2.js        7.02kb / brotli: 2.62kb
.svelte-kit/output/client/_app/start-1f66e358.js                17.59kb / brotli: 5.61kb
vite v2.4.4 building SSR bundle for production...
✓ 11 modules transformed.
.svelte-kit/output/server/app.js   10.98kb

Run npm run preview to preview your production build locally.

> Using @sveltejs/adapter-static
  ✔ done
```

Additional info

```
❯ npx envinfo --system --binaries --browsers --npmPackages "{svelte,@sveltejs/*,vite}"

  System:
    OS: macOS 11.5.1
    CPU: (8) x64 Apple M1
    Memory: 18.95 MB / 16.00 GB
    Shell: 5.8 - /bin/zsh
  Binaries:
    Node: 14.17.4 - /usr/local/bin/node
    Yarn: 1.22.10 - /usr/local/bin/yarn
    npm: 7.20.5 - /usr/local/bin/npm
  Browsers:
    Chrome: 92.0.4515.131
    Firefox: 91.0
    Safari: 14.1.2
  npmPackages:
    @sveltejs/adapter-static: 1.0.0-next.16 => 1.0.0-next.16
    @sveltejs/kit: 1.0.0-next.150 => 1.0.0-next.150
    svelte: ^3.34.0 => 3.42.1
```
