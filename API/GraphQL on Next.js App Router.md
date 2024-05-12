---
tags:
  - Nextjs
  - GraphQL
---

## Introduction

- [Route Handler](https://nextjs.org/docs/app/building-your-application/routing/router-handlers) enables you to provide API endpoint using Next.js App Router. There are at least two advantages:
	- You don't have to create a separate backend API project.
	- Frontend and API can share the same port
- This article describes basic approach to add [GraphQL](https://graphql.org/) API to Next.js Route Handler.

## Create Next.js project

- If you are working on the existing project, you can skip this section.

```sh
> npx create-next-app
√ What is your project named? ... graphql-route-handler
√ Would you like to use TypeScript with this project? ... Yes
√ Would you like to use ESLint with this project? ... Yes
√ Would you like to use Tailwind CSS with this project? ... Yes
√ Would you like to use `src/` directory with this project? ... Yes
√ Use App Router (recommended)? ... Yes
√ Would you like to customize the default import alias? ... No
Creating a new Next.js app in /your/path/graphql-route-handler.
(Omitted)
Success! Created graphql-route-handler at D:\projects\graphql-route-handler
> cd graphql-route-handler
> npm install graphql
```

## Add GraphQL endpoint

Suppose you would like to use `/graphql` as GraphQL endpoint. To this end, create a directory `graphql` under the directory `app` and create a file `route.ts` for Route Handler and `schema.graphql` for GraphQL schema:

```
graphql-route-handler/
+-src/
+-app/
+-graphql/
| +-route.ts
| +-schema.graphql
+-page.tsx
```

> ⚠️ Note that `page.js|jsx|ts|tsx` must not be present in `graphql` directory. See [Route Resolution](https://nextjs.org/docs/app/building-your-application/routing/router-handlers#route-resolution) section.
  
Define POST method to the given endpoint:
  
```tsx
// route.ts
export async function POST(request: Request) {
  // TODO
}
```

## Define GraphQL schema and resolvers

Suppose a simple GraphQL schema is defined is `schema.graphql`:

```graphql
# schema.graphql

type Query {
  getMessage: String
}

type Mutation {
  setMessage(message String): String
}
```
  
Build a schema and define resolvers in `route.ts`
  
```tsx
// route.ts

import { buildSchema } from 'graphql';
import { readFileSync } from 'fs';

const schema = buildSchema(readFileSync('app/graphql/schema.graphql', 'utf8'));
const resolvers = {
  getMessage: () => 'Hello, world!',
  setMessage: (message: string) => 'Goodbye, world!',
};
```
  
> ⚠️ Note that a path to a GraphQL schema must be relative to `src` directory.

## Finish GraphQL querying

And then parse request to JSON and feed into GraphQL:

```tsx
// route.ts

import { graphql } from 'graphql';
import { NextResponse } from 'next/server';

export async function POST(request: Request) {
  const { query, variables } = await request.json();
  const result = await graphql({
    schema,
    source: query,
    rootValue: resolvers,
    variableValues: variables,
  });
  return NextResponse.json(result);
}
```
