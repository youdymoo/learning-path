# Data Structures

## Data Sets

```js
// strings
let listOfNumbers = [2, 3, 5, 7, 11];
console.log(listOfNumbers[2]);
// → 5
console.log(listOfNumbers.length);
console.log(listOfNumbers["length"]);
// length not size (undefined)
```

## Methods

```js
// string
let doh = "Doh";
console.log(typeof doh.toUpperCase);
// → function
console.log(doh.toUpperCase());
// → DOH

// array (vector/stack)
let sequence = [1, 2, 3];
console.log(sequence.pop())
// → 3
sequence.push(4);
console.log(sequence);
// → [1, 2, 4]

// object
let day1 = {
  squirrel: false,
  events: ["work", "touched tree", "pizza", "running"]
};
delete day1.events;
console.log("events" in day1);
Object.assign(day1, {squirrel: true, extra: 4});
console.log(day1);
// → false
// → {squirrel: true, extra: 4}

// array of objects
let journal = [
  {events: ["work", "touched tree", "pizza",
            "running", "television"],
   squirrel: false},
  {events: ["work", "ice cream", "cauliflower",
            "lasagna", "touched tree", "brushed teeth"],
   squirrel: false},
  {events: ["weekend", "cycling", "break", "peanuts",
            "beer"],
   squirrel: true},
  /* and so on... */
];
```

Two objects with independent \(but same\) declarations are not the same object. Only if using the `=` operator. \(No deep comparison\)

## Classical JavaScript Loop

```js
for (let i = 0; i < JOURNAL.length; i++) {
  let entry = JOURNAL[i];
  // Do something with entry
}

for (let entry of JOURNAL) {
  console.log(`${entry.events.length} events.`);
}
```

## Search

```js
if (!events.includes(event)) { // search and return existance
        events.push(event);
events.indexOf(2); // search from the start
events.indexOf(2); // search from the end
```

## Queue

```js
let todoList = [];
todoList.push(task); // push_back;
todoList.shift(); // pop_front;
todoList.unshift(task); // push_front;
```

## Substring-like Methods

```js
console.log([0, 1, 2, 3, 4].slice(2, 4));
// → [2, 3]
console.log([0, 1, 2, 3, 4].slice(2));
// → [2, 3, 4]
array = ["a", "b", "c", "d", "e"];
console.log(array.slice(0, 2).concat(array.slice(2+ 1));
// → ["a", "b", "d", "e"]
```

Cannot add property to a string directly.

## Other methods

```js
console.log("  okay \n ".trim());
// → okay
console.log("LA".repeat(3));
// → LALALA
let words = ["never", "fully"];
console.log(["will", ...words, "understand"]);
```

Use `Math.random()` to generate random number from \(0,1\).

To create random number from \(0, 10\), use `console.log(Math.floor(Math.random() * 10));`

## JSON

> JavaScript Object Notation

`JSON.stringify`and`JSON.parse`

```
let string = JSON.stringify({squirrel: false,
                             events: ["weekend"]});
console.log(string);
// → {"squirrel":false,"events":["weekend"]}
console.log(JSON.parse(string).events);
// → ["weekend"]
```

## Exercises

```js
// one way to set the default argument
function range(start, end, step = start < end ? 1 : -1)

// reverse array (in place)
// can use unshift and push
// array.slice(0) good way to copy an array

// array to list and list to array
function arrayToList(array) {
  let list = null;
  for (let i = array.length - 1; i >= 0; i--) {
    list = {value: array[i], rest: list};
  }
  return list;
}

function listToArray(list) {
  let array = [];
  for (let node = list; node; node = node.rest) {
    array.push(node.value);
  }
  return array;
}

// deep comparison
function deepEqual(a, b) {
  if (a === b) return true;
  
  if (a == null || typeof a != "object" ||
      b == null || typeof b != "object") return false;

  let keysA = Object.keys(a), keysB = Object.keys(b);

  if (keysA.length != keysB.length) return false;

  for (let key of keysA) {
    if (!keysB.includes(key) || !deepEqual(a[key], b[key])) return false;
  }

  return true;
}
```



