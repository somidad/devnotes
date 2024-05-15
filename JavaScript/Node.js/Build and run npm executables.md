
## Build

### Declare executables in `package.json`

**Single executable**

```json
{
  "bin": "./path/to/file.js"
}
```

**Multiple executables**

```json
{
  "bin": {
    "package-name": "./path/to/file.js",
    "another-bin": "./path/to/another/file.js"
  }
}
```

### Shebang (`#!`) in executable file

Must start with the shebang:

```js
#!/usr/bin/env node
// JS code
```

To enable source maps

```js
#!/usr/bin/env -S node --enable-source-maps
// JS code
```

### If Webpack is used

Add *BannerPlugin* in `webpack.config.js` to add the shebang which Webpack removed

```js
const { BannerPlugin } = require("webpack");

module.exports = {
  plugins: [
    new BannerPlugin({
      banner: "#!/usr/bin/env node",
      raw: true
    })
  ]
};
```

## Run

**Single executable or executable with the package name**

```sh
npx package-name
```

**The other cases**

```sh
npx -p package-name executable-name
```
