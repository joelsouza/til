# Why does Array.filter(Number) filter zero out

JavaScript treats `0` as falsy.

```javascript
[0, 1, 2].filter(Number); // [1, 2]

// 0 is false as all others falsy JavaScript values:

// if (false)
// if (null)
// if (undefined)
// if (0)
// if (NaN)
// if ('')
// if ("")
// if (``)
```
