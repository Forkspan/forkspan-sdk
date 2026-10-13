# Forkspan SDK

`@forkspan/sdk` reads the results of a saved Forkspan comparison from your own backend, so you can
draw them with your own charts, colours and logos. This public repository distributes the SDK and
tracks its issues. Source development takes place in the Forkspan application repository.

## Install

```sh
npm i @forkspan/sdk
```

Requires Node.js 22 or later. The package is ESM and ships its TypeScript declarations.

## Read a comparison

Create a workspace API key in Forkspan (Settings, API keys). A viewer key is enough. Keep the key on
your server and never send it to a browser.

```ts
import { Client } from '@forkspan/sdk'

const forkspan = new Client({ apiKey: process.env.FORKSPAN_API_KEY! })

const comparison = await forkspan.getCompare('8f14e45f-ceea-467f-a0e6-1f6b3c4a2d10')

for (const bench of comparison.benches) {
  console.log(bench.config.model, bench.score, bench.costUsd)
}
```

The full reference, covering the options, what each result field means and the errors, is on
[the package page](https://www.npmjs.com/package/@forkspan/sdk).

## License

[MIT](LICENSE)
