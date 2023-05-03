---
tags:
  - javascript
---

# Javascript hints and tips
## Promises

The order of the results of the iterable passed into Promise.all is maintained.
refer https://stackoverflow.com/questions/28066429/promise-all-order-of-resolved-values



object & array destructuring
unpacking values from arrays and objects

eg
```javascript
//array destructuring
const arr = [1,2,3,4,5]
const [one, two] = arr;

// one = 1 & two = 2

const obj = {id: "id-01", name: "name-01"}
const { id } = obj;
```