
## Query

```
FOR d, e IN ANY|INBOUND|OUTBOUND documentId edgeCollectionName
  COLLECT AGGREGATE numEdges = LENGTH(1)
  RETURN numEdges
```

## Application: Finding a document with no edge

```
FOR doc IN collectionName
  let numEdges = (
    FOR d, e IN ANY|INBOUND|OUTBOUND doc._id edgeCollectionName
      COLLECT AGGREGATE numEdges = LENGTH(1)
      RETURN numEdges
  )[0]
  FILTER numEdges == 0
  RETURN doc
```
