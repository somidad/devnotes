
- [npm](https://www.npmjs.com/package/file-saver)
- [GitHuib](https://github.com/eligrey/FileSaver.js)

Example React code snippet:

```jsx
import { saveAs } from "file-saver";

function DownloadContent() {
  const download = () => {
    const blob = new Blob(["Hello, world!"], {type: "text/plain;charset=utf-8"});
    saveAs(blob, "hello, world.txt");
  }
  return (
    <button onClick={download}>Download</button>
  )
}
```
