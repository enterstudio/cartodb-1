cartodb tools
===


some tools for working with cartodb, for now works only with api keys.

Omit the callback from .exec and it will return a readable stream.

```js
var CartoDB = require('cartodb-tools');
var cartodb = new CartoDB('username', 'apikey');

cartodb.insert.into('table').values({
  foo: 'bar'
}).exec(function (err, resp) {
  // result of insert into table (foo) values ('bar');
  // also takes an array of values
});

cartodb.update.from('table').where([{foo: 'bar'}, {'thing': 'otherThing'}]).values({
  baz: 'bat'
}).exec(function (err, resp) {
  // result of update table set baz = 'bat' where foo = 'bar' or thing = 'otherThing';
});

cartodb.select.from('table').columns('foo').where({
  bar: 'bat',
  'thing': 'otherThing'
}).exec(function (err, resp) {
  // result of select foo from table where bar = 'bat' and thing = 'otherThing';
});

cartodb.delete.from('table').where({
  bar: 'bat',
  'thing': 'otherThing'
}).exec(function (err, resp) {
  // result of delete from table where bar = 'bat' and thing = 'otherThing';
});
```
