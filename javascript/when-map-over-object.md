# When Prefer Map Over Object

Use `Object` for records where you have a fixed and *finite number of properties/fields known* at author time, such as a config object. And *anything that is for one-time use* in general.

Use `Map` for *dictionaries* or hash maps where you have *a variable number of entries, with frequent updates*, whose keys might not be known at author time, such as an event emitter.

> Probably the most obvious downside of using objects for hash maps is that objects only allow keys that are strings and symbols. Any other types will be implicitly cast to string via the toString method.

```javascript
const foo = []
const bar = {}
const obj = {[foo]: 'foo', [bar]: 'bar'}

console.log(obj) // {"": 'foo', [object Object]: 'bar'}

const map = new Map();
map.set(null, 'a')
map.get(null) // a
map.has(null) // true
```
