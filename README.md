[![NPM Version](https://img.shields.io/npm/v/%40onhive.io%2Fastro-loader)](https://npmjs.com/package/@onhive.io/astro-loader)
[![codecov](https://codecov.io/gh/instytutfi/hive-astro-loader/graph/badge.svg?token=4dM1Jykhr4)](https://codecov.io/gh/instytutfi/hive-astro-loader)
[![GitHub Issues or Pull Requests](https://img.shields.io/github/issues-raw/instytutfi/hive-astro-loader)](https://github.com/instytutfi/hive-astro-loader/issues?q=sort%3Aupdated-desc+is%3Aissue+is%3Aopen)
[![Follow on Hive](https://img.shields.io/badge/follow-%40hive.coding-%23E31337?style=flat&logo=hive_blockchain&labelColor=%23111111)](https://ecency.com/@hive.coding)
![GitHub License](https://img.shields.io/github/license/instytutfi/hive-astro-loader)

# Hive Astro Loader

Astro Content Layer loader for the Hive blockchain

## Installation

```bash
npm install @onhive.io/astro-loader
```

Or use our favorite package manager.

## Usage

### Hive Blog Loader

In your Astro project, edit the `/src/content/config.ts`:

```ts
import { defineCollection } from "astro:content";
import { hiveBlogLoader } from "@onhive.io/astro-loader";

export const collections = {
  blog: defineCollection({
    type: "content_layer",
    loader: hiveBlogLoader("hive.coding") // Selected username
  })
};
```

For now only `hiveBlogLoader` is available, more coming soon!

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for more information.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
