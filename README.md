# Array Cardios

Exercises to practise array methods. Part of Wes Bos'
[JavaScript 30](https://javascript30.com/) course.

![Screenshot of array cardios in Firefox](https://image.prntscr.com/image/rtT7Be0NSzSmiscOf1sXmg.png)

## Notes

### array.prototype.filter()

`filter()` runs a function containing a test, loops over every element in an
array, and returns those that pass the test.

```js
const fifteen = inventors.filter(
  inventor => inventor.year >= 1500 && inventor.year < 1600
);
```

### array.prototype.map()

`map()` takes in an array, does something with it, and returns a new array of
the same length, i.e. it returns the same amount of elements that you give it.

To add a space when using map, you can either concatenate in a space `+ '' +` or
use ES6 template literals `${} ${}`.

```js
const fullNames = inventors.map(
  inventor => `${inventor.first} ${inventor.last}`
);
```

### array.prototype.sort()

`sort()` compares the values of pairs of elements in an array and bubbles them
up or down by returning 1 or -1.

```js
const ordered = inventors.sort(function(a, b) {
  if (a.year > b.year) {
    return 1;
  } else {
    return -1;
  }
});
```

or more succinctly

```js
const ordered = inventors.sort((a, b) => (a.year > b.year ? 1 : -1));
```

### array.prototype.reduce()

`reduce()` accepts two parameters (the accumulator and the current element
value). It runs a function on every element in an array accepting a new current
value each time. Finally it retuns a single total value.

```js
const totalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);
console.log(totalYears);
```

### console.table

`console.table()` logs your data to the console as a table.

### console.log({})

`console.log({})` will show you the name of the variable and its value.

### Node Lists

Node lists do not have all the methods arrays have. You can convert a node list
into an array using `Array.from()` or by creating an array and using ES6 spread
to spread every element into the array: `[...category.querySelectorAll('a')]`.

### array.prototype.some()

`some()` will check whether at least one element in your array meets what you
are looking for. It executes a callback function on every element until it finds
one that returns a truthy value.

```js
const isAdult = people.some(
  person => new Date().getFullYear() - person.year >= 19
);
console.log({ isAdult });
```

### array.prototype.every()

`every()` checks whether every element in an array passes the test you set in
the callback function.

```js
const allAdults = people.every(
  person => new Date().getFullYear() - person.year >= 19
);
console.log({ allAdults });
```

### array.prototype.find()

`find()` works similarly to `filter()` but return the first element that it
finds, rather than a subset of the array.

```js
const comment = comments.find(comment => comment.id === 823423);
console.log(comment);
```

### array.prototype.findIndex()

`findIndex()` returns the index of the first element in the array that meets the
provided test. It could be used to find the index of an element in order to
delete it, for example. You could then use splice or create a new array and
spread the desired elements into it.

```js
const index = comments.findIndex(comment => comment.id === 823423);
console.log(index);

// comments.splice(index, 1);

const newComments = [...comments.slice(0, index), ...comments.slice(index + 1)];
```
