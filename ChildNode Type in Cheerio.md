
When manipulating [Cheerio](https://cheerio.js.org), you may face `ChildNode` type. Mostly, [`children` property of `Element` type](https://cheerio.js.org/docs/api/classes/Element#children) is `ChildNode[]`.

But it should be noticed that this `ChildNode` type is not the [one comes from TypeScript](https://github.com/microsoft/TypeScript/blob/4ece0a381be3d925b12b9a1626583578b8735805/src/lib/dom.generated.d.ts#L5670).

It comes from [domhandler](https://www.npmjs.com/package/domhandler) package. So its structure, properties and methods may not be the same with the one from TypeScript.

In addition, domhandler uses [domelementtype](https://www.npmjs.com/package/domelementtype) package internally, behind the scenes, e.g. [`ElementType`](https://domhandler.js.org/enums/_internal_.ElementType.html)
