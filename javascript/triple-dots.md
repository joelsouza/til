# Better triple dot syntax (...) explanation

## rest vs. spread

- Rest syntax is for receiving data
- Spreading is for sending data

### Rest

#### Receiving as remaining arguments of a function

```javascript
function functionWithMultipleParams(arg1, ...remaining) {
  return { arg1, remaining}
}
```

#### Rest syntax in Array-destructuring

```javascript
  const [head, ...tail] = [1, 2, 3];
  // > head
  // 1
  // > tail
  // [ 1, 2 ]
```

#### Object-destructuring

```javascript
const { first: f, ...remaining } = {
  first: 'Jane',
  last: 'Doe',
  age: 43
};
// > f
// 'Jane'
// > remaining
// { last: 'Doe', age: 43 }
```

### Spreading

#### Spreading into a function call

```javascript
  function returnArgArray(...args) {
    return args
  }
  // > returnArgArray(...['x', 'y', 'z'])
  // [ 'x', 'y', 'z' ]
```

#### Spread Arrays into Array literals

```javascript
  [...['a', 'b'], 'c']
  // [ 'a', 'b', 'c' ]
```

#### Spread objects into object literals

```javascript
  { ...{ a: 1, b: 2 }, c: 3 }
  // { a: 1, b: 2, c: 3 }
```
