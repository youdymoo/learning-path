# Introduction to JavaScript

> When action grows unprofitable, gather information; when information grows unprofitable, sleep.
>
> -----Ursula K. Le Guin, _The Left Hand of Darkness_

The standard output of JavaScript is `console.log(something).`

Some code blocks are presented here.

```js
// type: number 
// JavaScript uses 64 bits to store numbers.
13 // integer (less than 9 quadrillion)
9.81 // fractional number
2.998e8 // exponent number
Infinity & -Infinity // Special number
NaN // not a number (0/0)
```

```js
// type: string
`backticks`
'single quote'
"double quote" // all strings
"\"\\n\"." // to represent "\n"
`backticks can have ${100/2}` // to represent 50
```

```js
// type: bool
console.log(3>2) == true
console.log("Aardvark" > "Zoroaster") == false // 'Z' < 'a'
console.log(NaN == NaN) == false
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

```js
// type: empty value
null
undefined
```



