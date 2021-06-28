<div align="center">
  <img width="200" height="200" src="https://worldvectorlogo.com/logos/html5.svg">
  <a href="https://github.com/evanw/esbuild">
    <img width="200" height="200"
      src="https://esbuild.github.io/favicon.svg">
  </a>
  <h1>esbuild HTML Plugin</h1>
  <p>Plugin that simplifies creation of HTML files to serve your esbuild bundles.</p>
</div>

## TOC <!-- omit in toc -->

- [Usage](#usage)
  - [Install](#install)
  - [API](#api)
- [Changelog](#changelog)
- [License](#license)

## Usage

### Install

```sh
# yarn
yarn add -D esbuild @esbuilder/html

# npm
npm install -D esbuild @esbuilder/html
```

### API

```ts
import esbuild from 'esbuild'
import { html } from '@esbuilder/html'

// serve mode
await esbuild.serve(
  {},
  {
    entryPoints: ['src/index.html'],
    plugins: [
      html({
        // required in serve mode
        serve: true,
        /**
         * Output filename pattern for `src` attribute in `script` tag,
         * the default value is `[name].[hash]`,
         * you can override it here.
         */
        // entryNames: 'js/[name]',
      }),
    ],
    outdir: 'dist',
    /**
     * required for keeping `dist/index.html` instead of `dist/index.{hash}.html`
     */
    assetNames: ['[name]'],
  },
)

// build mode
await esbuild.build({
  entryPoints: ['src/index.html'],
  plugins: [html()],
  outdir: 'dist',
  assetNames: ['[name]'],
})
```

```html
<!-- src/index.html -->
<!DOCTYPE html>
<html>
  <head>
    <!-- ... -->
  </head>
  <body>
    <script src="index.ts"></script>
  </body>
</html>
```

## Changelog

Detailed changes for each release are documented in [CHANGELOG.md](./CHANGELOG.md).

## License

[MIT][] © [JounQin][]@[1stG.me][]

[1stg.me]: https://www.1stg.me
[jounqin]: https://github.com/JounQin
[mit]: http://opensource.org/licenses/MIT
