## Issue running tests
```
npm run test

> my-first-worker@0.0.0 test
> vitest

DEV  v2.1.8 /Users/daniel/Development/Personal/cloudflare-vitest-assets-issue

[vpw:inf] Starting isolated runtimes for vitest.config.mts...
[mf:wrn] The latest compatibility date supported by the installed Cloudflare Workers Runtime is "2024-12-05",
but you've requested "2024-12-16". Falling back to "2024-12-05"...

⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯ Unhandled Errors ⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯

Vitest caught 1 unhandled error during the test run.
This might cause false positive tests. Resolve unhandled errors to make sure your tests are not affected.

⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯ Unhandled Error ⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯
TypeError: Cannot read properties of undefined (reading 'digest')
 ❯ hashPath node_modules/miniflare/dist/src/index.js:7772:62
 ❯ node_modules/miniflare/dist/src/index.js:7707:11
 ❯ walk node_modules/miniflare/dist/src/index.js:7681:3
 ❯ buildAssetManifest node_modules/miniflare/dist/src/index.js:7671:42
 ❯ Object.getServices node_modules/miniflare/dist/src/index.js:7589:56
 ❯ Miniflare2.#assembleConfig node_modules/miniflare/dist/src/index.js:9840:42
 ❯ Miniflare2.#assembleAndUpdateConfig node_modules/miniflare/dist/src/index.js:9940:20
 ❯ Mutex.runWith node_modules/miniflare/dist/src/index.js:3632:16
 ❯ Miniflare2.#waitForReady node_modules/miniflare/dist/src/index.js:10042:5
```

## Steps to reproduce

### Create new project
Run `npm create cloudflare@latest`

### Add assets config
Additional config in wrangler.toml
```
[assets]
directory = "./public"
binding = "ASSETS"
html_handling = "auto-trailing-slash"
not_found_handling = "none"
```

### Bump Wrangler
Bumping "wrangler" to the latest version "3.96.0" does not resolve the issue

### Create a public directory with one file

### Run tests
Run `npm run test`
