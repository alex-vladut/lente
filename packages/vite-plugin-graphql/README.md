# @lente/vite-plugin-graphql

Vite plugin that makes it easy to import `.graphql` files as [TypedDocumentNodes](https://github.com/dotansimha/graphql-typed-document-node), which enables Typescript autocomplete for your GraphQL queries.

The plugin utilizes the [graphql-let](https://github.com/piglovesyou/graphql-let) loader to generate types based on your configured GraphQL schema, ensuring that your code is always up-to-date and accurate. With this plugin, you can easily write robust and type-safe code that interfaces with your GraphQL API.

## Motivation

`@lente/vite-plugin-graphql` simplifies your GraphQL development experience by enabling fully typed imports of GraphQL queries. With this plugin, you can easily import GraphQL files and enjoy enhanced code readability and autocomplete.

![Importing graphql files](./import-graphql.gif 'Importing graphql files')

## Installation

Add `@lente/vite-plugin-graphql` NPM package to your project:

```bash
npm i -D @lente/vite-plugin-graphql
```

Create a `graphql-let.yml` file and configure where the GraphQL schema could be found. Check out `graphql-let` for more details on the available options.

```yml
schema:
  - ./schema.graphql

documents:
  - '**/*.graphql'

plugins:
  - typescript-operations
  - typed-document-node
```

And add the plugin to `vite.config.ts`:

```js
import { defineConfig } from 'vite';

import graphql from '@lente/vite-plugin-graphql';

export default defineConfig({
  plugins: [
    ...
    graphql({
      include: /\.(graphqls?|gql)$/i,
      babel: {
        presets: ['@babel/preset-typescript', '@babel/preset-react'],
      },
      rootContext: __dirname, // path to directory containing `graphql-let.yml`
    }),
  ],
  ...
});
```

### License

MIT
