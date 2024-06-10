
1. Add the followings to `next.config.mjs`:

This allows `npm run build` to generate GitHub Pages compatible folder and file structure. This articles assumes you want to publish it to `docs/` folder.

```diff
 import { env } from 'process';

 /** @type {import('next').NextConfig} */
 const nextConfig = {
+   output: 'export',
+   distDir: env.NODE_ENV === 'production' ? 'docs' : '.next',
 };

 export default nextConfig;
```

2. Add `.nojekyll` file under `public/` folder

This allows files under `docs/_next/` folder are accessible.

3. Add `CNAME` file under `public/` folder

```
your.domain.com
```

