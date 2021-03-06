# Program Structure

## Variables

```js
// all valid words
let one = 1, two = 2;
const greeting = "Hello "; // const binding
var name = "Ayda"; // pre-2015 JavaScript
```

## A full list of keywords

```js
break case catch class const continue debugger default
delete do else enum export extends false finally for
function if implements import interface in instanceof let
new package private protected public return static super
switch this throw true try typeof var void while with yield
```

## Simple Functions

```js
// pop-up function
prompt("Enter passcode"); // not used much because no control
// using example
let theNumber = Number(prompt("Pick a number"));
if (!isNaN(theNumber)) {
  console.log("Your number is the square root of " +
              theNumber * theNumber);
} else {
  console.log("Hey. Why didn't you give me a number?");
}nal (
```

## Statements

Conditional \(\``if`,`else`, and`switch`\) and looping \(`while`,`do`, and`for`\) statements.

## Exercises

```js
// to print 
#
##
###
####
#####
######
#######

// solution
for (var line = "#"; line.length < 8; line += "#")
  console.log(line);

// my solution
for (let level = 1; level <= 7; level++) {
  let output = '#';
  for (let number = 1; number < level; number++) {
    output += '#';
  }
  console.log(output);
}
```

```js
// solution
for (var n = 1; n <= 100; n++) {
  var output = "";
  if (n % 3 == 0)
    output += "Fizz";
  if (n % 5 == 0)
    output += "Buzz";
  console.log(output || n);
}

// my solution
for (let i = 1; i <= 100; i++) {
  if ((i % 3 == 0) && (i % 5 == 0)) console.log("FizzBuzz");
  else if (i % 5 == 0) console.log("Buzz");
  else if (i % 3 == 0) console.log("Fizz");
  else console.log(i);
}
```

```js
// solution
var size = 8;
var board = "";

for (var y = 0; y < size; y++) {
  for (var x = 0; x < size; x++) {
    if ((x + y) % 2 == 0)
      board += " ";
    else
      board += "#";
  }
  board += "\n";
}

console.log(board);
```

# Functions

Define

```js
const square = function(x) {
  return x * x;
};
console.log(square(12));
// → 144

const makeNoise = function() {
  console.log("Pling!");
};
makeNoise();
// → Pling!

function greet(who) {
  console.log("Hello " + who);
}

// return <without an expression> would return undefined
```

```js
// scope
let const // local to the block
var // global scope if not in a function
```

```js
// arrow functions
const power = (base, exponent) => {
  let result = 1;
  for (let count = 0; count < exponent; count++) {
    result *= base;
  }
  return result;
};

function power(base, exponent = 2) {
  let result = 1;
  for (let count = 0; count < exponent; count++) {
    result *= base;
  }
  return result;
}

// same thing
const square1 = (x) => { return x * x; };
const square2 = x => x * x;
```

## Closures

```js
function multiplier(factor) {
  return number => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));
// → 10
```

Recursive is generally 3 times slower than the looping version.

A very elegant function.

```js
function findSolution(target) {
  function find(current, history) {
    if (current == target) {
      return history;
    } else if (current > target) {
      return null;
    } else {
      return find(current + 5, `(${history} + 5)`) ||
             find(current * 3, `(${history} * 3)`);
    }
  }
  return find(1, "1");
}

console.log(findSolution(24));
// → (((1 * 3) + 5) * 3)
```



