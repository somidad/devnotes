
## Query

```
LET needle = "eedl"
LET haystack = ["needle", "in", "a", "haystack"]
RETURN haystack[** FILTER CONTAINS(CURRENT, needle)]
// Output: ["needle"]
```

## Variant: Case-insensitive

```
LET needle = "EEDL"
LET haystack = ["needle", "in", "a", "haystack"]
RETURN haystack[** FILTER CONTAINS(LOWER(CURRENT), LOWER(needle))]
// Output: ["needle"]
```

## References

1. [Array operators - Inline filter](https://www.arangodb.com/docs/stable/aql/advanced-array-operators.html#inline-filter)
1. [String functions - CONTAINS()](https://www.arangodb.com/docs/stable/aql/functions-string.html#contains)
1. [String functions - LOWER()](https://www.arangodb.com/docs/stable/aql/functions-string.html#lower)
