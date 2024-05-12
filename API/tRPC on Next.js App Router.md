---
tags:
  - Nextjs
  - tRPC
---

##  Create Next.js project

```sh
> npx create-next-app
What is your project named? my-app
Would you like to use TypeScript? No / Yes
Would you like to use ESLint? No / Yes
Would you like to use Tailwind CSS? No / Yes
Would you like to use `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
Would you like to customize the default import alias? No / Yes
What import alias would you like configured? @/*
```

I prefer to use `app/` directory instead of `src/`

## Install tRPC

```sh
npm install @trpc/server @trpc/client
```

## Project structure summary

```ascii
app/
+-api/
  +-[trpc]/
    +-route.ts: GET and POST route handlers
+-trpc.ts: client side boilerplate
server/
+-index.ts: server side API definition
+-trpc.ts: server side boilerplate
```

## Define tRPC on server side

- Create `server/` directory
- Create `server/trpc.ts`

```ts
import { initTPRC } from '@trpc/server';
const trpc = initTRPC.create();
export const { router, procedure } = trpc;
```

### Reference

- https://trpc.io/docs/server/routers#initialize-trpc

## Create `server/index.ts`

```ts
import * as trpc from '@trpc/server';
import { procedure, router } from './trpc';
const appRouter = router({
  greeting: procedure.query(() => 'hello tRPC v10!'),
});
export type AppRouter = typeof appRouter;
```

### Reference

- https://trpc.io/docs/server/routers#defining-a-router

## Define tRPC on client side

- Create `app/api/[trpc]/` directory
- Create `app/api/[trpc]/trpc.ts`

```ts
import { AppRouter } from "@/server";
import { createTRPCProxyClient, httpBatchLink } from "@trpc/client";
export const trpc = createTRPCProxyClient<AppRouter>({
  links: [
    httpBatchLink({
      url: "http://localhost:3000/api",
    }),
  ],
});
```

### Reference

- https://trpc.io/docs/client/vanilla/setup#3-initialize-the-trpc-client

## Create `app/api/[trpc]/route.ts`

```ts
import { appRouter } from "@/server";
import { fetchRequestHandler } from "@trpc/server/adapters/fetch";
const handler = (req: Request) =>
fetchRequestHandler({
  endpoint: "/api",
  req,
  router: appRouter,
  createContext: () => ({}),
});
export { handler as GET, handler as POST };
```

### Reference

- https://trpc.io/docs/server/adapters/nextjs#route-handlers
