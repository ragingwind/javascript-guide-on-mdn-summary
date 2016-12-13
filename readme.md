<!-- page_number: true -->
<!-- $size: 16:9 -->

# JavaScript: Summary of Javascript Guide on [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

> To give a presentation in short time, with additional descriptions to easier understand

---

# JavaScript is

- Object-oriented scripting language
- Functional programming (in technically)
- Small and lightweight can be running inside multiple environment
	- Browser, Node.js, Emebedded System
- Core standard library, and can be extended for a veriety of implementations
	- DOM control, Database, Network and System

---

# ECMAScript, ECMA-216 and JavaScript

- [ECMA-216](https://www.ecma-international.org/publications/standards/Ecma-262.htm) is a standards of [ECMA International](http://www.ecma-international.org/), standardized ECMAScript
- ECMAScript (or ES) is a standard for script languages evolving by TC39 and [proposals](https://github.com/tc39/proposals)
- JavaScript (or JS) is one of the implementations of the ECMAScript
- [ES2015/ECMAScript 6/ES6](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf)
- [Latest draft ECMAScript 2017 Language](https://tc39.github.io/ecma262/)

---

[![center original 30%](https://d262ilb51hltx0.cloudfront.net/max/800/1*v9AT7ZaJc6fR2MjYljGEzg.png)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

- Grammar and types
- Control flow and error handling
- Loops and iteration
- Functions
- Expressions and operators
- Numbers and dates
- Text formatting
- Regular expressions
- Indexed collections
- Keyed collections
- Classes

---

# Grammar and types

---

## Comments

```js
// a one line comment
 
/* this is a longer, 
   multi-line comment
 */
 
/* You can't, however, /* nest comments */ SyntaxError */
```

---

## Declarations

> var, let, const, scopde and hoisting

---

### Variables

```
// Start with letter, underscore(_), or dollor sign($)
var str = '';
var _ = 'underscore';
var $ = 'jquery';

// Subsequent charaters can be digist(0-9)
var str1 = '';

// Case sensitive, A-Z and a-z
var Str = '';

// ISO-8859-1 or Unicode letter
var 변수 = '변수';
var Š = 'Estonian';

```

---

### Declaring variables

```js
var x = 12; // with var, declare both local and global
x = 12; // without var, declare global
{
  let x = 12; // with let, decalre a block scope local variable
}
```

---

### Evaluating variables

```js
if (Math.pow(10, 1000) == Infinity) { // Infinity, 10 ^ 1000 is Infinity }

if (isNaN(NaN) || isNaN('string')) { // Not-A-Number }

if (typeof undefined === 'undefined' || this.GLOBAL_VAL === undefined) {
  // undefined object
}

if (typeof null === 'object' || null !== undefined || 
    null == undefined || this.GLOBAL_VAL === null) { 
  // assigned value of variable, var foo = null
}
```
---

### Variable scope

```js
// ECMAScript 2015 does not have block statement scope
if (true) {
  var x = 5;
}
console.log(x);  // x is 5

// let declaration introduced in ECMAScript 2015.
if (true) {
  let y = 5;
}
console.log(y);  // ReferenceError: y is not defined

// for the clean code in inner functions with let
for (let i = 1; i <= 5; i++) { }
```

---

### Variable hoisting

> hoisting: in JavaScript, you can refer to a variable declared later, without getting an exception, but defined with undefined not initialized value

```js
console.log(x === undefined); // true, x has defined with undefined
var x = 3;
```

---

### Function hoisting

```js
// Function declaration, only function declaration gets hoisted to the top
foo(); // "bar"

function foo() {
  console.log("bar");
}


// Function expression
baz(); // TypeError: baz is not a function

var baz = function() {
  console.log("bar2");
};
```

---

### Global variables

- Properties of the `global object`
- in Browser web pages, `window` is the `global object`
- in Node.js, `global` is the `global object`

---

### Constants


```js
// constant cannot change value through assignment or 
// be re-declared while the script is running
const PI = 3.14;

const c = 1;
{
  // const same as let block-scoped variable
  const c = 2;
}

console.log(c); // logs 1 and does not throw SyntaxError...
```

---

## Data structures and types

---

### Data types, Six data types that are primitives:

```js
let cond = false; // Boolean
let obj = null; // null
let obj = undefined; // undefined
let age = 30; // Number
let name = "Howdy"; // String

// Symbol (new in ECMAScript 2015). A data type whose instances 
// are unique and immutable
Symbol("foo") !== Symbol("foo");
const foo = Symbol();
let obj = { foo: "foo" };
Object.keys(obj); // []
Object.getOwnPropertySymbols(obj); // [ foo ]
```

---

### Data types, Object
```js
let obj = Object.create(Object.prototype, {
  prop: {
    configurable: true,
    get: function() { return this.value; },
    set: function(value) { this.value = value }
  }
});

obj.prop = 'value';
```
---

### Data type conversion

```js
// dynamically typed
var answer = 42;
answer = "Thanks for all the fish...";

// converts numeric values to strings
x = "The answer is " + 42 // "The answer is 42"
y = 42 + " is the answer" // "42 is the answer"

// other operators, does not convert numeric values to strings
"37" - 7 // 30
"37" + 7 // "377"

// retrieving a number from a string
"1.1" + "1.1" = "1.11.1"
(+"1.1") + (+"1.1") = 2.2 
```

---

## Literals

> fixed value and elements of enumerated types and compound values like Array and Object

```js
// Array
var coffees = ["French Roast", "Colombian", "Kona"];
var myList = ['home', , 'school', ]; // 'home', undefined, undefined, 'school', undefined

// Boolean
var cond = true;

// Integer
0 // decimal
+10 // decimal
3.1415926 // float
4.-3.1E+12 // float
015 // octal, 13
0x113 // hex, 4387
0b11 // binary, 3
```

---

```js
// Object
var sales = "Toyota";

function carTypes() {
  return "Honda";
}

var car = { myCar: "Saturn", getCar: carTypes(), special: sales };

console.log(car.myCar);   // Saturn
console.log(car.getCar);  // Honda
console.log(car.special); // Toyota
```

---


```js
// RegExp
var re = /ab+c/;

// String
"foo"
'foo'
console.log("John's cat".length);

// String template literal, [Template literals - JavaScript | MDN](https://goo.gl/0TTTDg)
`In JavaScript '\n' is a line-feed.`

// Multiline strings
`In JavaScript template strings can run
 over multiple lines, but double and single
 quoted strings cannot.`

// String interpolation
var name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`

// Using special characters in strings
"\tone line \n another line"
```

---

# [Control flow and error handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)

---

## Block statement

```js
{
  statement_1;
  statement_2;
  .
  statement_n;
}

// example 1
while (x < 10) {
  x++;
}

// example 2
var x = 1;
{
  var x = 2;
}
console.log(x); // outputs 2
```

---

## Conditional statements

---

### if...else statement

```js
if (num === false) { }
else if (obj === undefiend) { }
else if (person === null) { }
else if (count === 0) { }
else if (str === NaN) { }
else if (name === '') { }
else { }

// Boolean
var b = new Boolean(false);
if (b) { // this condition evaluates to true }
if (b == true) { // this condition evaluates to false }
```

---

### switch statement

```js
switch (fruittype) {
  case "Oranges":
    console.log("Oranges are $0.59 a pound.");
    break;
  case "Apples":
    console.log("Apples are $0.32 a pound.");
    break;
  case "Papayas":
    console.log("Mangoes and papayas are $2.79 a pound.");
    break;
  default:
   console.log("Sorry, we are out of " + fruittype + ".");
}
```

---

## Exception handling statements

```js
// several exceptions of varying types
try {
  throw new Error('Whoops!'); // Error type
  throw "Error2"; // String type
  throw 42; // Number type
  throw true; // Boolean type
  throw {toString: function() { return "I'm an object!"; } };
} catch (err) {
  console.log(err);
}
```

---

```js
// custom error
function MyError(message) {
	this.name = 'MyError';
	this.message = message || 'Default Message';
	this.stack = (new Error()).stack;
}

MyError.prototype = Object.create(Error.prototype);
MyError.prototype.constructor = MyError;

try {
  throw new MyError();
} catch (err) {
  console.log(err.name, err.message);
}
```

---

```js
// with The finally block
openMyFile();
try {
  writeMyFile(theData); //This may throw a error
} catch(e) {  
  handleError(e); // If we got a error we handle it
} finally {
  closeMyFile(); // always close the resource
}
```

---

## Promises

![center 160%](https://mdn.mozillademos.org/files/8633/promises.png)

> The Promise object is used for asynchronous computations. A Promise represents a value which may be available now, or in the future, or never.

---

```js
// Promise simple uses
function createPromise(cond) {
  return new Promise((resolve, reject) => {
    if (cond === undefined) { throw Error('No parameter') }
    setTimeout(() => {
       if (cond === true) { resolve(); } 
       else { reject(); }
    }, 500);
  });
}

function runPromise(cond) {
  createPromise(cond).then(() => { console.log('Resolved') })
    .catch(err => { console.log('Rejected or error', err && err.toString()) });
}

runPromise(); // Reject with error
runPromise(true); // Resolve
runPromise(false); // Reject without error
```

---

### Using [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) with Promise

```js
// download and set an image
var myImage = document.querySelector('img');

fetch('flowers.jpg')
.then(function(response) {
  return response.blob();
})
.then(function(myBlob) {
  var objectURL = URL.createObjectURL(myBlob);
  myImage.src = objectURL;
});
```
---

# [Loops and iteration](https://goo.gl/wXzLLW)

---

## for statement

```js
for (let step = 0; step < 5; step++) {
  // Runs 5 times, with values of step 0 through 4.
  console.log('Walking east one step');
}
```

---

## do...while statement

```js
var i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5);
```

---

## while statement

```js
while (n < 3) {
  n++;
}

// infinity loop
while (true) {
  console.log("Hello, world");
}
```

---

## break and continue statement

```js
// break
for (var i = 0; i < a.length; i++) {
  if (a[i] == theValue) {
    break;
  }
}

// continue
var i = 0;
var n = 0;
while (i < 5) {
  i++;
  if (i == 3) {
    continue;
  }
  n += i;
}
```

---

## for...in statement

> iterates a specified variable over all the enumerable properties of an object

```js
// iterate properties of an object
const obj = {
	name: 'name',
	age: 30
};

for (let p in obj) {
  // obj.name : name
  // obj.age : 30
  console.log('obj.' + p, ':', obj[p]);
}

// iterate indexes of an array
for (let n in [1, 2, 3, 4, 'true']) {
  console.log(n); // 0, 1, 2, 3, 4
}
```

---

## for...of statement

> creates a loop Iterating over iterable objects including Array, Map, Set, arguments object and so on

```js
let arr = [3, 5, 7];
arr.foo = "hello";

console.log(arr); // [ 3, 5, 7, foo: 'hello' ]

for (let i in arr) {
  console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); // logs 3, 5, 7
}
```

---

# Function

---

## Defining functions

```js
// function declarations
function square(number) {
  return number * number;
}

// function expression
var square = function(number) { return number * number };

// function expression with anonymous function
var sum = function(num1, num2) { return num1 + num2 };
```

---

## Calling functions

```js
// normal call
square(5);

// function declaration can be hoisted
console.log(square(5));
function square(n) { return n * n }

// function expression cannot be hoisted
console.log(square); // square is hoisted with an initial value undefined.
console.log(square(5)); // TypeError: square is not a function
var square = function (n) { 
  return n * n; 
}
```

---

```js
// calling it self
function factorial(n){
  if ((n === 0) || (n === 1))
    return 1;
  else
    return (n * factorial(n - 1));
}
```

--- 

## Function scope

```js
// defined in the global scope
var num1 = 20, num2 = 3, name = "Chamahk";

// defined in the global scope
function multiply() { return num1 * num2; }

multiply(); // Returns 60

// nested function example
function getScore () {
  var num1 = 2, num2 = 3; // defined in the function
  function add() { return name + " scored " + (num1 + num2); }
  
  return add();
}

getScore(); // Returns "Chamahk scored 5"
```

---

## Scope and the function stack

```js
// a three way of calling function
function bar(stop) {
  if (stop === true) {
    // arguments.callee, in case of anonumous function
    arguments.callee(true); 
  }
};

var foo = bar;

// calling by function name
bar();

// calling by in-scope variable that refers to the function
foo();
```

---

## Nested functions and closures

```js
function addSquares(a,b) {
  function square(x) {
    return x * x;
  }
  // inner function can be accessed only 
  // from statements in the outer function.
  return square(a) + square(b);
}
a = addSquares(2,3); // returns 13
b = addSquares(3,4); // returns 25
c = addSquares(4,5); // returns 41
```

---

```js
function outside(x) {
  function inside(y) {
    // inner function forms a closure:
    // the inner function can use the arguments
    // variables of the outer function. in this case, x
    return x + y; // closure must preserve the arguments 
                  // and variables in all scopes it reference
  }
  return inside;
}

fn_inside = outside(3); // give me a function that adds 3
result = fn_inside(5); // returns 8
result1 = outside(3)(5); // returns 8
```

---

## Closures

> Closures are functions that refer to independent (free) variables (variables that are used locally, but defined in an enclosing scope, its `lexical scoping`). In other words, these functions 'remember' the environment in which they were created.

---

```js
// The outer function defines a variable called "name"
var pet = function(name) {
  // The inner function has access 
  // to the "name" variable of the outer function
  var getName = function() {
    // has a reference to that scope of "name"
    // and that reference is called closure
    return name;
  }
  // Return the inner function, thereby exposing it to outer scopes
  return getName;
},
myPet = pet("Vivie");
   
myPet(); // Returns "Vivie", closure was juet observed
```

---

```js
// more complex code above
var createPet = function(name) {
  var sex;
  
  return {
    setName: function(newName) { name = newName }, // has a reference to name
    getName: function() { return name }, // has a reference to name
    getSex: function() { return sex }, // has a reference to sex
    setSex: function(newSex) { sex = newSex } // has a reference to sex
  }
}

var pet = createPet("Vivie");
pet.getName();                  // Vivie
pet.setName("Oliver");
pet.setSex("male");
pet.getSex();                   // male
pet.getName();                  // Oliver
```

---

```js
// define a same name variable with a defined variable at enclose function
var createPet = function(name) {  // Outer function defines a variable called "name"
  return {
    setName: function(name) {    // Enclosed function also defines a variable called "name"
      name = name;               // ??? How do we access the "name" defined by the outer function ???
    }
  }
}
```

---

## Using the arguments object

> arguments of a function are maintained in an array-like object(not Array)

```js
function myConcat(separator) {
  var result = ""; // initialize list
  var i;
  // iterate through arguments
  for (i = 1; i < arguments.length; i++) {
    result += arguments[i] + separator;
  }
  return result;
}

// returns "red, orange, blue, "
myConcat(", ", "red", "orange", "blue");
```

---

```js
function callee(num) {
  console.log(num, this); // 10 [Function: caller]
}

function caller() {
  callee.apply(caller, arguments);
}

caller(10);
```

---

## Function parameters

```js
// default parameter
function multiply(a, b = 1) {
  return a*b;
}

multiply(5); // 5

// rest paramters
function multiply(multiplier, ...theArgs) {
  console.log(typeof theArgs); // object
  return theArgs.map(x => multiplier * x);
}

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

---

## Arrow functions

> shorter syntax compared to function expressions and lexically binds the `this` value, are always anonymous.

```js
var a = [ "Hydrogen", "Helium", "Lithium", "Beryllium"];

var a2 = a.map(function(s){ return s.length });
var a3 = a.map( s => s.length ); // no return place at a line
```

---

```js
// In ECMAScript 3/5
function Person() {
  var self = this; // Some choose `that` instead of `self`. 
                   // Choose one and be consistent.
  self.age = 0;

  setInterval(function growUp() {
    // The callback refers to the `self` variable of which
    // the value is the expected object.
    self.age++;
  }, 1000);
}

// In ECMAScript 2015
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| properly refers to the person object
  }, 1000);
}

var p = new Person();
```

---

## Predefined functions

```
// 3
console.log(eval('var foo = 3; console.log(foo)'));

// 10, 10, NaN
console.log(parseInt('10'), Number.parseInt('10'), Number.parseInt('NaN'));

// 3.14 3.14
console.log(parseFloat('3.14'), Number.parseFloat('3.14'));

const url = 'google.com/한글';
const enc = encodeURIComponent(url);
const dec = decodeURIComponent(enc);

// google.com%2F%ED%95%9C%EA%B8%80 google.com/한글
console.log(enc, dec);
```

---

# [Expressions and operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

---

## Assignment operators

```js
let x, y;
console.log(x = 10, y = 30, x = y); // Assignment, = 30
console.log(x = 10, y = 30, x += y); // Addition, 10 + 30 = 40
console.log(x = 10, y = 30, x -= y); // Subtraction ,10 - 30 = -20
console.log(x = 10, y = 30, x *= y); // Multiplication , 10 * 30 = 300
console.log(x = 10, y = 30, x /= y); // Division , 10 / 30 = 0.3333
console.log(x = 10, y = 30, x %= y); // Remainder , 10 % 30 = 10
console.log(x = 1, y = 1, x <<= y); // Left shift , 1 << 1 = 2
console.log(x = 1, y = 1, x >>= y); // Right shift , 1 >> 1 = 0
console.log(x = 1, y = 1, x >>>= y); // Unsigned right shift, 1 >>> 1 = 0
console.log(x = 1, y = 0, x &= y); // Bitwise AND, 1 & 0 = 0
console.log(x = 1, y = 0, x ^= y); // Bitwise XOR, 1 ^ 0 = 1
console.log(x = 1, y = 0, x |= y); // Bitwise OR, 1 | 0 = 1
```

---

### Destructuring

> extract data from arrays or objects into distinct variables

```js
var foo = ["one", "two", "three"];

// without destructuring
var one   = foo[0];
var two   = foo[1];
var three = foo[2];

// with destructuring
var [one, two, three] = foo;
```

---

```js
var a, b, rest;
[a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2

// destructing with rest
[a, b, ...rest] = [1, 2, 3, 4, 5];
console.log(a); // 1
console.log(b); // 2
console.log(rest); // [3, 4, 5]

({a, b} = {a:1, b:2});
console.log(a); // 1
console.log(b); // 2
```

---

## Comparison operators

```js
console.log(1 == '1'); // true
console.log(1 === '1'); // false, strict equal
console.log(1 != '1'); // false
console.log(1 !== '1'); // true, strict not equal
console.log(1 > 2); // false
console.log(1 >= 1); // true
console.log(1 < 2); // true
console.log(1 <= 1); // true
```

---

## Arithmetic operators

```js
let x, y;
console.log(3 % 2); // 1, Remainder
console.log(x = 1, x++); // 1, Increment
console.log(x = 1, ++x); // 2
console.log(x = 1, x--); // 1, Decrement
console.log(x = 1, --x); // 0
console.log(-1); // -1, Unary negation
console.log(-(-1)); // 1
console.log(+1); // 1 Unary plus
```

---

## Bitwise operators

```js
console.log(1 & 0); // 0, Bitwise AND
console.log(1 | 0); // 1, Bitwise OR
console.log(1 ^ 0); // 1, Bitwise XOR
console.log(~0); // -1, Bitwise NOT
console.log(1 << 1); // 2, Left Shift
console.log(-1 >> 1); // -1, Sign-propagating right shift
console.log(1 >>> 1); // 0, Zero-fill right shift
```

---

## Logical operators

```js
console.log(true && true);     // t && t returns true
console.log(true && false);    // t && f returns false
console.log(false && true);     // f && t returns false
console.log(false && (3 == 4)); // f && f returns false
console.log("Cat" && "Dog");    // t && t returns Dog
console.log(false && "Cat");    // f && t returns false
console.log("Cat" && false);    // t && f returns false
```

---

## String operators

```js
console.log("my " + "string"); // console logs the string "my string".

var mystring = "alpha";
mystring += "bet"; // evaluates to "alphabet" and assigns this value to mystring.
```

---

## Conditional (ternary) operator

```js
const status = (age >= 18) ? "adult" : "minor";
```

---

## Comma operator

```js
for (var i = 0, j = 9; i <= j; i++, j--) {
  console.log("a[" + i + "][" + j + "]= " + a[i][j]);
}
```

---

## Unary operators

- delete
- typeof
- 
---


### delete
```js
// delete
x = 42;
var y = 43;
myobj = new Number();
myobj.h = 4;    // create property h
delete x;       // returns true (can delete if declared implicitly)
delete y;       // returns false (cannot delete if declared with var)
delete Math.PI; // returns false (cannot delete predefined properties)
delete myobj.h; // returns true (can delete user-defined properties)
delete myobj;   // returns true (can delete if declared implicitly)
```

---

```js
// delete array elements
var trees = ["redwood", "bay", "cedar", "oak", "maple"];
delete trees[3];
if (3 in trees) {
  // this does not get executed
}
```

---

### typeof

```js
var myFun = new Function("5 + 2");
var shape = "round";
var size = 1;
var today = new Date();

typeof myFun; // returns "function"
typeof shape; // returns "string"
typeof size; // returns "number"
typeof today; // returns "object"
typeof doesntExist; // returns "undefined"
typeof true; // returns "boolean"
typeof null; // returns "object"
typeof 62; // returns "number"
typeof 'Hello world'; // returns "string"
```

---

### void

```html
// void() return undefined it result in browser stays on the same page
<a href="javascript:void(0)">Click here to do nothing</a>
<a href="javascript:void(document.form.submit())">Click here to submit</a>
```

---

## Relational operators

### in

> returns true if the specified property is in the specified object

```js
var trees = ["redwood", "bay", "cedar", "oak", "maple"];
0 in trees;        // returns true
3 in trees;        // returns true
6 in trees;        // returns false
"bay" in trees;    // returns false (you must specify the index number,
                   // not the value at that index)
"length" in trees; // returns true (length is an Array property)

// built-in objects
"PI" in Math;          // returns true
var myString = new String("coral");
"length" in myString;  // returns true

// Custom objects
var mycar = { make: "Honda", model: "Accord", year: 1998 };
"make" in mycar;  // returns true
"model" in mycar; // returns true
```

---

### instanceof

> returns true if the specified object is of the specified object type

```js
var theDay = new Date(1995, 12, 17);
if (theDay instanceof Date) {
  // statements to execute
}
```

---

## [Operator precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table)

---

## Primary expressions

### this

> refer to the current object

```js
function validate(obj, lowval, hival){
  // obj is <input>
  if ((obj.value < lowval) || (obj.value > hival))
    console.log("Invalid Value!");
}

<p>Enter a number between 18 and 99:</p>
<input type="text" name="age" size=3 onChange="validate(this, 18, 99);">
```

---

### Grouping operator

```js
var a = 1;
var b = 2;
var c = 3;

// default precedence
a + b * c     // 7
// evaluated by default like this
a + (b * c)   // 7

// now overriding precedence 
// addition before multiplication   
(a + b) * c   // 9

// which is equivalent to
a * c + b * c // 9
```

---

## Left-hand-side expressions

### new

> to create an instance of a user-defined object type or of one of the built-in object types

```js
var objectName = new objectType([param1, param2, ..., paramN]);
```

### super

> to call functions on an object's parent. It is useful with classes to call the parent constructor

```js
class Dog {
  constructor(props) {
    super(props);
  }
}
```

---

### Spread operator

> allows an expression to be expanded in places where multiple arguments (for function calls) or multiple elements (for array literals) are expected.

```js
// with array
var parts = ['shoulder', 'knees'];
var lyrics = ['head', ...parts, 'and', 'toes'];


// with function call
function f(x, y, z) { }
var args = [0, 1, 2];
f(...args)
```

---

# Numbers and dates

---

## Numbers

```js
// decimal
1234567890
0888 // 888 parsed as decimal, 8 is not octal
0777 // parsed as octal in non-strict mode (511 in decimal)

// binary
var FLT_SIGNBIT  = 0b10000000000000000000000000000000; // 2147483648
var FLT_EXPONENT = 0b01111111100000000000000000000000; // 2139095040
var FLT_MANTISSA = 0B00000000011111111111111111111111; // 8388607

// octal
var n = 0755; // 493
var a = 0o10; // ES6: Octal

// hexdecimal
0xFFFFFFFFFFFFFFFFF // 295147905179352830000
0x123456789ABCDEF   // 81985529216486900
0XA   // 10
1E3   // 1000
2e6   // 2000000
0.1e2 // 10
```

---

## Number object

```js
var biggestNum = Number.MAX_VALUE;
var smallestNum = Number.MIN_VALUE;
var infiniteNum = Number.POSITIVE_INFINITY;
var negInfiniteNum = Number.NEGATIVE_INFINITY;
var notANum = Number.NaN;

console.log(Number('123')); // 123
console.log(Number('foo')); // NaN
console.log(Number('10.1')); // 10.1
console.log(Number.parseInt('10.2')); // 10
console.log(Number.parseFloat('10.0'), Number.parseFloat('10.0').toFixed(1)); // 10 '10.0'
console.log(Number.parseFloat('10.3')); // 10.3
```

---

## Math object

```js
console.log(Math.max(1, 100)); // 100
console.log(Math.min(1, 100)); // 1
console.log(Math.cos(2 * Math.PI)); // 2 * PI Radians is 1turn
console.log(Math.sqrt(9)); // 3
console.log(Math.sqrt(2)); // 1.4142135623730951
console.log(Math.round(20.49)); // 20
console.log(Math.round(20.5)); // 21
console.log(Math.round(42)); // 42
console.log(Math.round(-20.5)); // 20
console.log(Math.round(-20.51)); // 21
console.log(Math.ceil(.95)); // 1
console.log(Math.ceil(4)); // 4
console.log(Math.ceil(7.004)); // 8
console.log(Math.floor(.95)); // 0
console.log(Math.floor(4)); // 4
console.log(Math.floor(7.004)); // 7
console.log(Math.floor(Math.random() * (100 - 1) + 1));
```

---

## [Date object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

> Date object range is -100,000,000 days to 100,000,000 days relative to 01 January, 1970 UTC.

```js
// the number of milliseconds elapsed since 1 January 1970 00:00:00 UTC
console.log(Date.now());

const d = new Date();
console.log(d.getFullYear(), d.getMonth() + 1, d.getDate());
console.log(d.getHours(), d.getMinutes() , d.getSeconds());

const birthday = new Date('December 17, 1995 03:24:00');
console.log(birthday);
// [Intl · nodejs/node Wiki](https://goo.gl/8eh6xi)
console.log(birthday.toLocaleString('ko-KR'));
```

---

# [Text formatting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Text_formatting)

---

## String

```js
'foo'
"bar"
'中文 español deutsch English हिन्दी العربية português বাংলা русский 日本語 ਪੰਜਾਬੀ 한국어 தமிழ் עברית💯🎉🐶👍'
// Hexadecimal escape sequences
'\xA9' // "©"
// Unicode escape sequences
'\u00A9' // "©"
// Unicode code point escapes
'\u{2F804}' // 你
// the same with simple Unicode escapes
'\uD87E\uDC04' // 你

```

---

## String objects

```js
var s = new String("foo"); // Creates a String object
console.log(s); // Displays: { '0': 'f', '1': 'o', '2': 'o'}
typeof s; // Returns 'object'

var s1 = "2 + 2"; // Creates a string literal value
var s2 = new String("2 + 2"); // Creates a String object
eval(s1); // Returns the number 4
eval(s2); // Returns the string "2 + 2"

var mystring = "Hello, World!";
var x = mystring.length;
mystring[0] = 'L'; // This has no effect
mystring[0]; // This returns "H"
```

---

```js
// String, Accessing
console.log('cat'.charAt(1), 'cat'[1]); // a a

// String, Compare
const a = 'a', b = 'b';
if (a < b) { console.log(a + ' is less than ' + b) } // a is less than b
else if (a > b) { console.log(a + ' is greater than ' + b) } 
else { console.log(a + ' and ' + b + ' are equal.') }

console.log(a.localeCompare(b)); // -1

// String.concat
var hello = 'Hello, ';
console.log(hello.concat('Kevin', ' have a nice day.')); // Hello, Kevin have a nice day.

// String.indexOf
console.log('Blue Whale'.indexOf('Blue')); // 0
console.log('Blue Whale'.indexOf('blue')); // -1
console.log('Blue Whale'.indexOf('Blute')); // -1
console.log('Blue Whale'.indexOf('e')); // 3
console.log('Blue Whale'.lastIndexOf('e')); // 9
```

---

```js
// String.match
// [see Chapter 3.4.5.1', 'Chapter 3.4.5.1', '.1', 
// index: 22, input: 'For more information, see Chapter 3.4.5.1' ]
console.log('For more information, see Chapter 3.4.5.1'
            .match(/see (chapter \d+(\.\d)*)/i));
// [ 'A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e' ]
console.log('ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
            .match(/[A-E]/gi));

// String.replace
// Twas the night before Chrismas...
console.log('Twas the night before Xmas...'.replace(/xmas/i, 'Chrismas'));
// Twas the night before Chrismas...
console.log('Twas the night before Xmas...'.replace('Xmas', 'Chrismas'));

// String.split
console.log('Hello World. How are you doing?'.split(' ')); // [ 'Hello', 'World.', 'How', 'are', 'you', 'doing?' ]
console.log('Hello World. How are you doing?'.split(' ', 3)); // [ 'Hello', 'World.', 'How' ]
console.log('Hello World. How are you doing?'.split(/\s/)); // [ 'Hello', 'World.', 'How', 'are', 'you', 'doing?' ]

// String.slice(begin, [end])
console.log('1234567890'.slice(0, 2)); // 12
console.log('1234567890'.slice(-2)); // 90
console.log('1234567890'.slice(0, -1)); // 123456789
```

---

```js
// String.substr(start, [length])
console.log('1234567890'.substr(0, 2)); // 12
console.log('1234567890'.substr(-2)); // 90
console.log('1234567890'.substr(1, 3)); // 234

// String.substring(start, [end])
console.log('1234567890'.substring(0, 2)); // 12
console.log('1234567890'.substring(-1)); // 1234567890, less than 0 or NaN, it is treated as 0
console.log('1234567890'.substring(1, 3)); // 23

// String.toLowerCase / toUpperCase
console.log('ABCDEF'.toLowerCase(), 'ABCDEF'.toLowerCase().toUpperCase()); // abcdef ABCDEF

// String.trim
console.log('   AB C DF   '.trim()); // AB C DF
```

---

### Multi-line template literals

- Multi-lines

    ```js
    console.log("string text line 1\n\
    string text line 2");
    // "string text line 1
    // string text line 2"

    console.log(`string text line 1
    string text line 2`);
    // "string text line 1
    // string text line 2"
    ```

- Embedded expressions

    ```js
    var a = 5, b = 10;
    console.log("Fifteen is " + (a + b) + " and\nnot " + (2 * a + b) + ".");
    // "Fifteen is 15 and
    // not 20."

    console.log(`Fifteen is ${a + b} and\nnot ${2 * a + b}.`);
    // "Fifteen is 15 and
    // not 20."
    ```

---

# [Regular Expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)


```js
// creating a regular expression
var re = /ab+c/;
var re = new RegExp("ab+c");

// simple sampe
const re = /\w+/i;
console.log('abcdef'.match(re)); // [ 'abcdef', index: 0, input: 'abcdef' ]

const reObj = new RegExp('\\w+', 'i');
console.log('abcdef'.match(reObj)); // [ 'abcdef', index: 0, input: 'abcdef' ]
```

---

# [Indexed collections](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Indexed_collections)

---

## Array object

```js
// create a array object
var arr = new Array(arrayLength);
var arr = Array(arrayLength);

// this has exactly the same effect
var arr = [];
arr.length = arrayLength;
```

---

```js
// accessing
const fruits = ['Apple', 'Banana'];
console.log(fruits, fruits.length, fruits[0], fruits[1], fruits[fruits.length - 1]);
console.log(fruits.indexOf('Apple'));
console.log(fruits.length);

// loop over with Array.forEach
fruits.forEach(fruit => {
	console.log(fruit);
});

// loop over with for of
for (const fruit of fruits) {
	console.log(fruit);
}

// loop over with for in
for (const i in fruits) {
	console.log(fruits[i]);
}
```

---

```js
// manupulating
console.log(fruits.push('Orange'), fruits);
console.log(fruits.pop(), fruits);
console.log(fruits.shift(), fruits);
console.log(fruits.unshift('Strawberry'), fruits);
console.log(fruits.join(', '));
console.log(fruits.slice());
console.log(fruits.splice(0, 1), fruits);
console.log(fruits.concat(['Peach']));
```

---

### Multi-dimensional arrays

```js
var a = new Array(4);
for (i = 0; i < 4; i++) {
  a[i] = new Array(4);
  for (j = 0; j < 4; j++) {
    a[i][j] = "[" + i + "," + j + "]";
  }
}

Row 0: [0,0] [0,1] [0,2] [0,3]
Row 1: [1,0] [1,1] [1,2] [1,3]
Row 2: [2,0] [2,1] [2,2] [2,3]
Row 3: [3,0] [3,1] [3,2] [3,3]
```

---

### Typed Arrays

>  array-like objects and provide a mechanism for accessing raw binary data through [ArrayBuffer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)

![150% center](https://mdn.mozillademos.org/files/8629/typed_arrays.png)

---

# [Keyed collections](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Keyed_collections)

> collections are ordered by a key; Map and Set objects contain elements which are iterable in the order of insertion

---

## Map object

> simple key/value map and can iterate its elements in insertion order

```js
var sayings = new Map();
sayings.set("dog", "woof");
sayings.set("cat", "meow");
sayings.set("elephant", "toot");
sayings.size; // 3
sayings.get("fox"); // undefined
sayings.has("bird"); // false
sayings.delete("dog");
sayings.has("dog"); // false

for (var [key, value] of sayings) {
  console.log(key + " goes " + value);
}
// "cat goes meow"
// "elephant goes toot"

sayings.clear();
sayings.size; // 0
```

---

```js
const facebook = new Map();

console.log(facebook.set('Kim', { name: 'Kim', age: 30 }), facebook); // Map { 'Kim' => { name: 'Kim', age: 30 } } Map { 'Kim' => { name: 'Kim', age: 30 } }
console.log(facebook.size); // 1
console.log(facebook.get('Kim')); // { name: 'Kim', age: 30 }

// loop over with key/value iterable object
for (const [key, value] of facebook) { console.log(key, value); } // Kim { name: 'Kim', age: 30 }

// loop over with keys iterable object
for (const key of facebook.keys()) { console.log(key, facebook.get(key)); } // Kim { name: 'Kim', age: 30 }

// loop over with values iterable object
for (const value of facebook.values()) { console.log(value); } // { name: 'Kim', age: 30 }

// loop over with key/value iterable object
for (const [key, value] of facebook.entries()) { console.log(key, value); } // Kim { name: 'Kim', age: 30 }

// loop over
facebook.forEach((value, key) => { console.log(key, value) }); // Kim { name: 'Kim', age: 30 }
```

---

## WeakMap object

> collection of key/value pairs in which the keys are objects only and the values can be arbitrary values in limited use case. The WeakMap API is the same as the Map API but one difference to Map objects is that WeakMap keys are not enumerable

```js
const privates = new WeakMap();

function Public() {
  const me = {
    // Private data goes here
  };
  privates.set(this, me);
}

Public.prototype.method = function () {
  const me = privates.get(this);
  // Do stuff with private data in `me`...
};

module.exports = Public;
```

---

## Set object

> collections of values. You can iterate its elements in insertion order. A value in a Set may only occur once

```js
var mySet = new Set();
mySet.add(1);
mySet.add("some text");
mySet.add("foo");

mySet.has(1); // true
mySet.delete("foo");
mySet.size; // 2

for (let item of mySet) { console.log(item) }
// 1
// "some text"

// converting between Array and Set
Array.from(mySet);
[...mySet2];
mySet2 = new Set([1,2,3,4]);
```

---

# [Working with objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

> JavaScript is designed on a simple object-based paradigm. An object is a collection of properties, and a property is an association between a name (or key) and a value

---

## Objects and properties

```js
// create an objec
var myCar = new Object();
myCar.make = "Ford"; // same with myCar["make"] = "Ford"
myCar.model = "Mustang"; // same with myCar["model"] = "Mustang";
myCar.year = 1969; // same with myCar["year"] = 1969;
myCar.color; // undefined

// object property name can be any valid JavaScript string
var myObj = new Object(), str = "myString"
var rand = Math.random(), obj = new Object();

myObj.type              = "Dot syntax";
myObj["date created"]   = "String with space";
myObj[str]              = "String value";
myObj[rand]             = "Random Number";
myObj[obj]              = "Object";
myObj[""]               = "Even an empty string";

console.log(myObj);
```

---

## Enumerate the properties of an object

```js
// for...in with iterate over all the enumerable properties of an object
function showProps(obj, objName) {
  var result = "";
  for (var i in obj) {
    if (obj.hasOwnProperty(i)) {
      result += objName + "." + i + " = " + obj[i] + "\n";
    }
  }
  return result;
}

// Object.keys()
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// Object.getOwnPropertyNames()
var arr = ['a', 'b', 'c'];
console.log(Object.getOwnPropertyNames(arr).sort()); 
// logs ["0", "1", "2", "length"]
```

---

## Creating new objects

### Using object initializers

```js
var myHonda = {color: "red", wheels: 4, engine: {cylinders: 4, size: 2.2}};
```

### Using a constructor function

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

var mycar = new Car("Eagle", "Talon TSi", 1993);
```

---

### Using the Object.create method

```js
// Animal properties and method encapsulation
var Animal = {
  type: "Invertebrates", // Default value of properties
  displayType : function() {  // Method which will display type of Animal
    console.log(this.type);
  }
}

// Create new animal type called animal1 
var animal1 = Object.create(Animal);
animal1.displayType(); // Output:Invertebrates

// Create new animal type called Fishes
var fish = Object.create(Animal);
fish.type = "Fishes";
fish.displayType(); // Output:Fishes
```

---

## Inheritance

> All objects in JavaScript inherit from at least one other object. The object being inherited from is known as the [prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype), and the inherited properties can be found in the prototype object of the constructor

---

### Defining properties for an object type

```js
function Car(name) {
	this.name = name;
}

Car.prototype.color = null;
const car = new Car('honda');
car.color = 'black';

console.log(car);
```

---

### Defining methods

```js
function displayCar() {
  var result = "A Beautiful " + this.year + " " + this.make
    + " " + this.model;
  pretty_print(result);
}

var myObj = {
  myMethod: displayCar
};

function Car(make, model, year, owner) {
  this.make = make;
  this.model = model;
  this.year = year;
  this.owner = owner;
  this.displayCar = displayCar;
}

```
----

### Defining getters and setters

```js
var d = Date.prototype;
Object.defineProperty(d, "year", {
  get: function() { return this.getFullYear() },
  set: function(y) { this.setFullYear(y) }
});

var now = new Date();
console.log(now.year); // 2000
now.year = 2001; // 987617605170
console.log(now);
// Wed Apr 18 11:13:25 GMT-0700 (Pacific Daylight Time) 2001
```

---

### Deleting properties

```js
// Creates a new object, myobj, with two properties, a and b.
var myobj = new Object;
myobj.a = 5;
myobj.b = 12;

// Removes the a property, leaving myobj with only the b property.
delete myobj.a;
console.log ("a" in myobj) // yields "false"
```

---

### Comparing Objects

```js
// Two variables, two distinct objects with the same properties
var fruit = {name: "apple"};
var fruitbear = {name: "apple"};

fruit == fruitbear // return false
fruit === fruitbear // return false

// two variables, a single object
var fruit = {name: "apple"};
var fruitbear = fruit;  // assign fruit object reference to fruitbear

// here fruit and fruitbear are pointing to same object
fruit == fruitbear // return true
fruit === fruitbear // return true
fruit.name = "grape";
console.log(fruitbear);    // yields { name: "grape" } instead of {
```

---

# Class

> Classes are in fact "special functions", are not a new way of oop, provide a much simpler and clearer syntax to create objects and deal with inheritance

---

## Defining classes

### Class declarations

```js
class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

// hosting
var p = new Polygon(); // ReferenceError
class Polygon {}
```

---


### Class expressions

```js
// unnamed
var Polygon = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};

// named
var Polygon = class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

---

## Class body and method definitions

### Prototype methods

```js
// The bodies of class declarations and class 
// expressions are executed in strict mode.
class Polygon {
  // special method for creating and initializing 
  // an object created with a class
  constructor(height, width) {
    super(height, width) // constructor can use the super keyword 
                         // to call the constructor of a parent class
    this.height = height;
    this.width = width;
  }
  
  get area() { return this.calcArea() }
  calcArea() { return this.height * this.width }
}

const square = new Polygon(10, 10);

console.log(square.area);
```

---

### Static methods

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  static distance(a, b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;

    return Math.sqrt(dx*dx + dy*dy);
  }
}

const p1 = new Point(5, 5);
const p2 = new Point(10, 10);

console.log(Point.distance(p1, p2));
```

---

### Boxing with prototype and static methods

> When a static or prototype method is called `without an object valued` "this" (or with "this" as boolean, string, number, undefined or null)

```js
class Animal {
  speak() {
    return this;
  }
  static eat() {
    return this;
  }
}

let obj = new Animal();
console.log(obj.speak()); // Animal {}, with object value

let speak = obj.speak;
console.log(speak()); // undefined

let eat = Animal.eat;
console.log(eat()); // undefined
```

---

### Sub classing with extends

```js
class Animal { 
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(this.name + ' makes a noise.');
  }
}

class Dog extends Animal {
  speak() {
    console.log(this.name + ' barks.');
  }
}

var d = new Dog('Mitzie');
d.speak();
```

---


### Species

> You might want to return Array objects in your derived array class MyArray. The species pattern `lets you override default constructors`

```js
class MyArray extends Array {
  // Overwrite species to the parent Array constructor
  static get [Symbol.species]() { return Array; }
}

var a = new MyArray(1,2,3);
var mapped = a.map(x => x * x);

console.log(mapped instanceof MyArray); // false
console.log(mapped instanceof Array);   // true
```

---

### Super class calls with super

```js
class Cat { 
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(this.name + ' makes a noise.');
  }
}

class Lion extends Cat {
  speak() {
    super.speak();
    console.log(this.name + ' roars.');
  }
}
```

---

### Mix-ins

> subclasses or mix-ins are templates for classes.

```js
var calculatorMixin = Base => class extends Base {
  calc() { console.log('calculatorMixin::calc') }
};

var randomizerMixin = Base => class extends Base {
  randomize() { console.log('randomizerMixin::randomize') }
};

class Foo {
	add() { console.log('Foo::origin') }
}
class Bar extends calculatorMixin(randomizerMixin(Foo)) { }

const b = new Bar();

b.add();
b.randomize();
b.calc();
```

---

# License

The content of this code and description itself of [MDN](https://developer.mozilla.org/en-US/) is licensed under [MDN Licenses](https://developer.mozilla.org/en-US/docs/MDN/About#Copyrights_and_licenses), and the rest of source code and annotations display at content is licensed under the [ Creative Commons Attribution 3.0 license](https://creativecommons.org/licenses/by/3.0/us/deed.en_US).