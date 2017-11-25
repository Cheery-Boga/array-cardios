# Array Cardios

Exercises to practise array methods. Part of Wes Bos'
[JavaScript 30](https://javascript30.com/) course.

![Screenshot of array cardios in Firefox](https://image.prntscr.com/image/rtT7Be0NSzSmiscOf1sXmg.png)

## Notes

### array.filter()

`filter()` runs a function containing a test, loops over every item in an array,
and returns those that pass the test.

```js
const fifteen = inventors.filter(
  inventor => inventor.year >= 1500 && inventor.year < 1600
);
```

### array.map()

`map()` takes in an array, does something with it, and returns a new array of
the same length, i.e. it returns the same amount of items that you give it.

To add a space when using map, you can either concatenate in a space `+ '' +` or
use ES6 template literals `${} ${}`.

```js
const fullNames = inventors.map(
  inventor => `${inventor.first} ${inventor.last}`
);
```

### array.sort()

`sort()` compares the values of pairs of items in an array and bubbles them up
or down by returning 1 or -1.

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

### array.reduce()

`reduce()` accepts two parameters (the accumulator and the current item value).
It runs a function on every item in an array accepting a new current value each
time. Finally it retuns a single total value.

```js
const totalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);
console.log(totalYears);
```

### console.table

`console.table()` logs your data to the console as a table.

### Node Lists

Node lists do not have all the methods arrays have. You can convert a node list
into an array using `Array.from()` or by creating an array and using ES6 spread
to spread every item into the array: `[...category.querySelectorAll('a')]`.
