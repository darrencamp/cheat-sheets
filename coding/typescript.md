---
tags:
  - javascript
  - typescript
---

## Convert enum to array

```typescript
export enum MyEnum {
	"test" = 0,
	"hello" = 1,
	"worlf" = 2
}
Object.entries[MyEnum].map(([key,value]) => ({name: key, value}));
```

can use the resultant array as part of a dropdown/select ui item

note: the above will return an array for **all** combinations of name/value pairs ie
```
["test", 0]
["hello", 1]
["world", 2]
[1, "test"]
[2, "hello"]
[3, "world" ]
```

so if just the string to number mappings are required will need to filter the Object.entries array with something like this:

```typescript

Object.entries[MyEnum]
	.filter(([key, value]) => !isNan(key))
	.map(([key,value]) => ({name: key, value}));

```