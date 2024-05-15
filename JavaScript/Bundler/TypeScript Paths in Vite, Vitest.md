
```sh
npm install --save-dev vite-tsconfig-paths
```

`vite.config.ts`:

```diff
 import { defineConfig } from 'vite'
+import tsconfigPaths from 'vite-tsconfig-paths'

 export default defineConfig({
+  plugins: [tsconfigPaths()],
 })
```

`vitest.config.ts`:

```diff
 import { defineConfig } from 'vitest'
+import tsconfigPaths from 'vite-tsconfig-paths'

 export default defineConfig({
+  plugins: [tsconfigPaths()],
 })
```