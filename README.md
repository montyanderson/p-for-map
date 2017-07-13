# p-for-map

Run through a for loop concurrently with Promises.

## Usage

``` javascript
// serial

const users = [];

for(let i = 0; i < 10; i++) {
	users[i] = await getUser(i);
}

// concurrent

const users = await pForMap(
	0,
	i => i < 10,
	i => ++i,
	async i => users[i] = await getUser(i)
);
```

## API

### pForMap(init, condition, expression, handler)`

Returns a `Promise` that resolves to the resultant array of values.

#### init

Type: any<br>
Example: `0`

Initial iterator value; what `i` is set to initially.

#### condition

Type: `Function`<br>
Example: `i => i < 10`

Expected to return a `Boolean`.

#### expression

Type: `Function`<br>
Example: `i => ++i`

Returns the next `i` value.

#### handler

Type: `Function`<br>
Example: `i => console.log(i)`

Expected to return a `Promise`.
