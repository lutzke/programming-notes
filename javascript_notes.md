## JavaScript

*notes from learning on Codecademy*



### some quick notes on syntax

* line endings: semicolon

* comments:
	* `//` or `/* */`
	
* `true` and `false` are lowercase

* variable names are camelCase
	* variable names may not begin with numbers
	
* `else if` is used for conditionals (NOT `elif`)

* equality check is `===` **three** equal signs!
	* `!==` inequality is also three characters
	
	* for more info on `==` vs. `===` in JS: 
	
	  https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a?gi=6ab085353db1



### data types

* primitives:
	* number
	* string
	* boolean
	* null
	* undefined
	* symbol: a unique identifier
* others:
	* object: a collection of related data



### basic operations and general advice

#### logging, or printing to the console

* logging to console: `console.log()`
* note that both properties, e.g. `string.length` and methods, e.g. `console.log()` use the dot operator. but properties and methods are not the same!
  * methods have the brackets, even if called without an argument; `console.log()` is a method

#### typeof

* `typeof` is an operator, not an object, method, etc. and it is used like so: `typeof myVar`, **NOT like** `typeof(myVar)`.

##### numbers

* note that JS allows negative zero, e.g. by evaluating `-20 % 5`
* this operator exists: `someNum += 1;`
	* so do `-=`, `*=` and `/=`
	* and so do `++` (increment) and `--` (decrement)

##### strings

* template literals are similar to f-strings in Python
	* they may be used to interpolate or insert values into strings, e.g.: `I own a pet ${myPet}.`
	* template literals are wrapped by single **backticks:** no need to escape quotes
	* putting variables into a string is called string interpolation


#### properties

* strings have the property `length`: e.g. `'Hello'.length`


#### built-in methods and objects

* `Math.random()` returns a random number between 0 (inclusive) and 1 (exclusive.)
* `Math.floor()` rounds down to the nearest whole number
* `Number` and `Math` are not the same!


#### variables

* `let` and `const` are prefered over `var` from JS ES6 onwards
	* variables assigned with `let` are scoped to their block (enclosed by `{ }` curly braces), wheras `var` scopes a variable to the enclosing function
* variables initialize to *undefined*, if no value is assigned
* `let` signals that a variable can be reassigned a different value
* keywords are only needed to initialize a variable; a variable, someVar, can be reassigned like so: `someVar = 42;`

* trying to reassign a variable made with `const` (a constant) throws a TypeError
* consts *must* be assigned a value. failing to do this will throw a SyntaxError



### history

#### ES6 and before

* JS created in '95 by Netscape
* When you see ES6 or JavaScript ES6, it means that that version of JavaScript is following the specifications in the sixth edition of ECMAScript!
  * If you want to create an app or program you can use JavaScript — if you want to create a new scripting language you can follow the guidelines in ECMAScript.
* ES2015 = ES6
* ES6 was the biggest update to JS since it was first standardized in '97
  * It included:
    * let, const keywords
    * arrow functions syntax
    * classes
    * parameters w/ default values
    * and more.
* node.js was introduced in 2009



### logic

#### if, else...

```JavaScript
if (true) {
	console.log("It's really true!");
} else {
	console.log("It's false...");
}
```



#### comparison

* equality check is `===` **three** equal signs!
	* this is called the *identity operator*
	  * checks for strict equality: both expressions must be the same type, and evaluate to the same value
	* `!==` inequality is also three characters
	* for more info on `==` vs. `===` in JS: https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a?gi=6ab085353db1
* a comparison evaluates to true or false depending on whether it's... you guessed it... a true or false statement



#### logical operators

* three logical operators:
	* `&&` and - two things are both true
	* `||` or - at least one is true
	* `!` not - inversion

##### truthiness and falsiness

* falsy values include:
  * `0`
  * empty strings
  * `null`
  * `undefined`
  * `NaN`

##### short-circuit evaluation

* ```JavaScript
  let tool = '';
  let writingUtensil = tool || 'pen';
  ```

  * `||` (OR) statement checks left side first, so the left value is assigned if it true. else, the right value is assigned.

##### ternary operator

```javascript
let isNightTime = true;
 
if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

...is equivalent to:

```javascript
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

**how/when to use ternary operator**

a good example of how to use it:

```javascript
someNum = Math.random();
animal = someNum >= 0.5 ? 'Alpaca' : 'Zebra';
console.log(animal);
```

* explanation:

  > a ternary expression is not a replacement for an if/else construct - it's an equivalent to an if/else construct that returns a value. That is, an if/else clause is code, **a ternary expression is an expression, meaning that it returns a value.**

  * ...from: https://stackoverflow.com/questions/2932754/ternary-operators-in-javascript-without-an-else

##### switch (keyword)

* an alternative to crazy long lists of `else if`'s is the switch statement

```javascript
let groceryItem = 'papaya';
 
switch (groceryItem) {
  case 'lime':
    console.log('Limes are $1.49');
    break;
  case 'papaya':
    console.log('Papayas are $1.29');
    break;
  default:
    console.log('Invalid item');
    break;
}
```

* note the use of the `break` keyword above in each case. don't forget this!
  * https://stackoverflow.com/a/39757921




### functions

* basic examples:

```javascript
function greetWorld(name = 'world') {
  console.log(`Hello, ${name}!`)
}
```

```javascript
function rectangleArea(width, height) {
  return width * height;
}
```



* hoisting

  ```javascript
  greetWorld('David');
  
  function greetWorld(name = 'world') {
    console.log(`Hello, ${name}!`)
  }
  ```

  * ...is generally, not recommended

  * https://developer.mozilla.org/en-US/docs/Glossary/Hoisting

    * JavaScript **Hoisting** refers to the process whereby the interpreter appears to move the *declaration* of functions, variables or classes to the top of their scope, prior to execution of the code.

      Hoisting allows functions to be safely used in code before they are declared.

      Variable and class *declarations* are also hoisted, so they too can be referenced before they are declared. **Note that doing so can lead to unexpected errors, and is not generally recommended.**

* default parameters are specified with an `=` equals sign, the assignment operator

* **undefined** is returned if no return value is specified

* functions may, of course, call other functions (or even themselves!)



#### arrow notation

* remember to use the "fat" arrow **`=>`** not the skinny one `->`

see https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions for more info*

```javascript
// Traditional Anonymous Function
function (a, b) {
  return a + b + 100;
}

// Arrow Function
(a, b) => a + b + 100;

// Traditional Anonymous Function (no arguments)
let a = 4;
let b = 2;
function () {
  return a + b + 100;
}

// Arrow Function (no arguments)
let a = 4;
let b = 2;
() => a + b + 100;
```

basic syntax:

```javascript
param(s) => expression (to be returned)
```

default params are supported:

```javascript
(a=400, b=20, c) => expression
```



##### more concise syntax

syntax can be more concise, depending on...

**number of parameters the function will take in:**

* zero:

  ```javascript
  const functionName = () => {};
  ```

* one:

  ```javascript
  const functionName = paramOne => {};
  ```

  * note that `paramOne` does not need any `()` parentheses around it

* two:

  ```javascript
  const functionName = (paramOne, paramTwo) => {};
  ```

**number of lines:**

* single-line:

  ```javascript
  const doubleNumber = number => number + number;
  ```

  * no `{}` curly braces needed
  * no `return` statement needed; it's implied that `number + number` is returned, because it's the only statement inside the function

* compare that to multi-line:

  ```javascript
  const sumNumbers = number => {
    const sum = number + number;
    return sum;
  };
  ```

  * ***return is not implied, because there are multiple statements, so `return` must explicitly be used!***

#### function expressions

simple example:

```javascript
const getRectArea = function(width, height) {
  return width * height;
};

console.log(getRectArea(4,3)); // Output: 12
```

* function expressions are *not* hoisted (they *must* be defined before they are used)

* function expressions seem to mainly be useful for creating anonymous functions to be called when some event is fired, e.g.:

  ```javascript
  myButton.onclick = function() {
    alert('hello');
  }
  ```



### scope (and blocks)

* be careful with collisions:
  * **a local variable can (and will) overwrite a global variable with the same name**

> Tightly scoping your variables will greatly improve your code in several ways:
>
> - It will make your code more legible since the blocks will organize your code into discrete sections.
> - It makes your code more understandable since it clarifies which variables are associated with different parts of the program rather than having to keep track of them line after line!
> - It’s easier to maintain your code, since your code will be modular.
> - It will save memory in your code because the variable(s) will cease to exist after the block finishes running.

> **If a variable does not need to exist outside a block— it shouldn’t!**



### higher-order functions

> A *higher-order function* is a function that either accepts functions as parameters, returns a function, or both

> JavaScript functions behave like any other data type in the language; we can assign functions to variables, and we can reassign them to new variables.

> We call the functions that get passed in as parameters and invoked *callback functions* because they get called during the execution of the higher-order function

> When we pass a function in as an argument to another function, we don’t invoke it (...) With callbacks, we pass in the function itself by typing the function name *without* the parentheses 

```javascript
function myFunction() {
  console.log("It's functional!");
}
const myVar = myFunction; // Notice the lack of parentheses!
myVar();
console.log(myVar.name); // Output: myFunction
```

* **notice the lack of parentheses**
  * we are assigning the function itself, not its return value, to this variable
  * `myFunction()` evaluates to the function's return value
  * `myFunction` is the function itself

> In JavaScript, functions are *first class objects*. This means that, like other objects you’ve encountered, JavaScript functions can have properties and methods.

* anonymous functions can be first order functions, or arguments, too!

more information: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function



### arrays

basic example: 

```javascript
let concepts = ['creating arrays', 'array structures', 'array manipulation']
```

* arrays can store any data types (including strings, numbers, and booleans). arrays are ordered, meaning each item has a numbered position.
* attempting to access an index that does not exist returns `undefined`

##### pass-by-reference

* mutating an array inside of a function
  * the mutation (change) will be preserved outside of the function after it is called

##### const

* **arrays declared using `const` are mutable, meaning elements in the array may be re-assigned**

  ```javascript
  const numbers = [40, 41, 42];
  numbers[1] = [55]; // This works
  numbers = [54, 55, 56]; // TypeError: Assignment to constant variable.

##### .length

* ...is a built-in property of any array

  ```javascript
  const numbers = [40, 41, 42];
  console.log(numbers.length); // Output: 3
  ```

##### nested arrays

```javascript
const nestedArr = [[1], [2, 3]];
console.log(nestedArr[1][0]); // Output: 2
```



#### array methods

* complete list: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

> * `.pop()` and `.push()` mutate the array on which they’re called. However, there are times that we don’t want to mutate the original array and we can use non-mutating array methods. Be sure to check MDN to understand the behavior of the method you are using.
> * Some arrays methods that are available to JavaScript developers include: `.join()`, `.slice()`, `.splice()`, `.shift()`, `.unshift()`, and `.concat()` amongst many others. Using these built-in methods make it easier to do some common tasks when working with arrays.

##### .push()

* add items to the end of an array

  ```javascript
  const itemTracker = ['item 0', 'item 1', 'item 2'];
   
  itemTracker.push('item 3', 'item 4');
   
  console.log(itemTracker); 
  // Output: ['item 0', 'item 1', 'item 2', 'item 3', 'item 4'];
  ```

##### .pop()

* remove the last item of an array

* **`.pop()` returns the removed item**

  ```javascript
  const newItemTracker = ['item 0', 'item 1', 'item 2'];
   
  const removed = newItemTracker.pop();
   
  console.log(newItemTracker); 
  // Output: [ 'item 0', 'item 1' ]
  console.log(removed);
  // Output: item 2
  ```

##### .shift()

* removes (and returns) the first element of an array

##### .unshift()

* adds one or more elements to the beginning of an array
* returns the new length of the array

##### .slice()

> * The **`slice()`** method returns a shallow **copy of a portion of an array** into a new array object selected from `start` to `end` (`end` not included) where `start` and `end` represent the index of items in that array. The original array will not be modified.

```javascript
const numbers = [40, 41, 42, 43, 44];

console.log(numbers.slice(2)); // Output: [42, 43, 44]
console.log(numbers.slice(2, 4)); // Output: [42, 43]
console.log(numbers.slice(-2)); // Output: [43, 44]
console.log(numbers.slice(2, -1)); // Output: [42, 43]
```

* slice(inclusive, exclusive)

##### .indexOf()

* returns an integer: 
  * the **first** index at which a given element can be found in the list
  * `-1` if it can't be found



### loops

#### for loop

> A `for` loop contains three expressions separated by `;` inside the parentheses:
>
> 1. an *initialization* starts the loop and can also be used to declare the iterator variable.
> 2. a *stopping condition* is the condition that the iterator variable is evaluated against— if the condition evaluates to `true` the code block will run, and if it evaluates to `false` the code will stop.
> 3. an *iteration statement* is used to update the iterator variable on each loop.

```javascript
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}
```

#### while loop

```javascript
while (someConditionIsTrue) {
  doSomething();
}
```

#### do while loop

```javascript
do {
  something();
} while (someConditionIsTrue);
```

#### break keyword

* break out of the enclosing loop's block
  * excludes if/else/other blocks which don't belong to loops



### iterators

#### `.forEach()`

* execute the same code for each element of an array

* it's a method that can be called on something to be iterated over (e.g. array) which accepts a callback function as an argument

* always returns undefined

  ```javascript
  const fruits = ['mango', 'papaya', 'pineapple', 'apple'];
  fruits.forEach(fruit => console.log(`I want to eat a ${fruit}`));
  // Output: I want to eat a mango \ I want to eat a papaya \ (...etc.)
  ```



#### `.map()`

* a new array is returned, with the value returned for each element put into the new array.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]; 
  const bigNumbers = numbers.map(number => number * 10);
  console.log(bigNumbers);
  // Output: [ 10, 20, 30, 40, 50 ]
  ```



#### `.filter()`

* returns a new array...
  * ...after certain elements are filtered out
  * elements that cause the callback function to return `true` are added to the new array

```javascript
const words = ['chair', 'music', 'pillow', 'bricks', 'pen', 'door']; 
const shortWords = words.filter(word => {
  return word.length < 6;
});
// Returns [ 'chair', 'music', 'pen', 'door' ]
```



#### `.findindex()`

* find location of an element in an array
  * returns **the index of** the first element that causes the callback function to return `true`

```javascript
const jumbledNums = [123, 25, 78, 5, 9]; 
const lessThanTen = jumbledNums.findIndex(num => num < 10);
// Returns 3 (NOT 5!)
```

* yes, this returns the **index** of the element, **not** the element itself!
* returns `-1` if no element in the array causes the callback function to return `true`



#### `.reduce()`

* returns a single value after iterating over an array

  ```javascript
  const numbers = [1, 2, 4, 10];
   
  const summedNums = numbers.reduce((accumulator, currentValue) => {
    return accumulator + currentValue
  })
   
  console.log(summedNums) // Output: 17
  ```

  * `accumulator` defaults to `array[0]` on first call
  * `currentValue` defaults to `array[1]` on first call



#### `.every()`

* returns `true` if every value in the array causes the callback function to return `true`. returns `false` otherwise
  * kind of like AND `&&`




#### `.some()`

* returns `true` if at least one value in the array causes the callback function to return `true`. returns `false` otherwise
  * kind of like OR `||`




### objects

* objects may be assigned to variables using `{}` curly braces

* objects have **properties**, which consist of a key and a value

* keys and values are separated by **colons**

* keys are strings, but only need quotes around them if they contain spaces or special characters

* key-value pairs are separated by **commas**

  ```javascript
  let object = {
    key: value,
    'key two': 42
  };
  ```

* e.g.

  ```javascript
  let cube = {
    faces: 6,
    type: 'regular polyhedron'
  };
  ```

* data in objects is unordered

  * it **can't** be indexed into like `object[0]`

* this unordered data is organized into key-value pairs



#### properties 

* ...may be accessed in a couple of different ways:

##### dot notation

* e.g.

  ```javascript
  console.log(spaceship.color);
  ```

* when trying to access a property that does not exist, `undefined` is returned

##### bracket notation

* e.g. 

  ```javascript
  console.log(spaceship['Fuel Type']);

* bracket notation must be used when accessing keys that have numbers, spaces, or special characters in them

* bracket notation is also useful when passing in a variable (string) to select a key, e.g.

  ```javascript
  let returnProperty = (objectName, propertyName) => objectName[propetyName];
  returnProperty(spaceship, 'homePlanet'); // returns 'Earth'



#### mutability 

* objects may have properties re-assigned, or entirely new ones assigned
* dot or bracket notation may be used to assign a new value to an existing property, or add an entirely new property to the object
* we can't reassign an object declared with const, but we can still mutate it
  * add new properties
  * modify existing ones

```javascript
const spaceship = {type: 'shuttle'};
spaceship = {type: 'alien'}; // TypeError: Assignment to constant variable.
spaceship.type = 'alien'; // Changes the value of the type property
spaceship.speed = 'Mach 5'; // Creates a new key of 'speed' with a value of 'Mach 5'
```

* properties can be deleted with the `delete` operator:

  ```javascript
  delete spaceship['Secret Mission'];
  ```



#### methods

* **while a property is something an object has, a method is something an object *does*.**

* when the data stored in an object is a function, it's called a method

* `console.log('Hello, world!')` uses a method!

  * `console` is a global JavaScript object, and `log` is one of its methods

* methods are also key-value pairs

  * the key is the method's name

  * the value is the function (an anonymous function expression)

    ```javascript
    const alienShip = {
      invade: function () {
        console.log('All your base are belong to us!')
      }
    };
    ```

  * with new syntax in ES6, we can do:

    ```javascript
    const alienShip = {
      invade () {
        console.log('All your base are belong to us!')
      }
    };
    ```




#### nested objects

* nested objects may be accessed like so:

  ```javascript
  const apple = { 
    color: 'Green',
    price: {
      bulk: '$3/kg',
      smallQty: '$4/kg'
    }
  };
  console.log(apple.price.bulk); // '$3/kg'
  console.log(apple['price'].smallQty); // '$4/kg'
  ```

  * nested objects are accessed from outside to inside, left to right

* arrays of objects are possible; see `passengers` below:

  ```javascript
  const spaceship = {
    passengers: [{
      name: 'Benjamin',
      degree: 'Microbiology',
      seat: '12B',
    }, {
      name: 'Jane',
      degree: 'Organic Chemistry',
      seat: '13B',
    }],
    crew: {
      captain: {
        name: 'Sarah',
        degree: 'Computer Engineering',
      },
      telescope: {
        yearBuilt: 2018,
        model: '91031-XLT',
        focalLength: 2032,
      },
    },
  };
  
  console.log(`Captain ${spaceship.crew.captain.name} reporting for duty!`);
  // Output: Captain Sarah reporting for duty!
  ```



#### pass by reference

* objects are passed by reference in JavaScript
  * meaning, when an object (even one declared using `const`) is passed into a function as an argument, a pointer is given to the object's location in memory
  * any changes to the object will be made to this location in memory, i.e. to the original object


#### looping through objects

* example:

  ```javascript
  for (const passenger in spaceship.passengers) {
    console.log(`${passenger}: ${spaceship.passengers[passenger].name}`);
  };
  ```




### `this`

* the `this` keyword references the calling object, and allows us to access its properties

* when is it useful? **line 7** in the following example

  * e.g. without `this`:

    > ` "ReferenceError: dietType is not defined" `

    ```javascript
    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      },
      diet() {
        console.log(dietType); // <-----
      }
    };
    goat.diet(); 
    ```

    with `this`:

    > `herbivore`

    ```javascript
    const goat = {
      dietType: 'herbivore',
      makeSound() {
        console.log('baaa');
      },
      diet() {
        console.log(this.dietType); // <-----
      }
    };
     
    goat.diet(); 
    ```

* why is `this` necessary in the above example?

  * inside the **scope** of the `diet()` method, other properties of the `goat` object aren't accessible

* arrow functions, objects and `this`
  * arrow functions should ***not*** be used as methods, because they lack a binding for `this`
    * don't use arrow functions inside objects!



### objects, continued

#### privacy

* some properties should not be able to be accessed and updated

  * we may only certain properties to be mutable
  * this is called privacy, which is a feature many languages have built-in with objects
    * JavaScript does not

* instead of having a built-in mechanism for privacy, JavaScript developers use a naming convention to signal that a property should be immutable: a leading underscore `_`

  * e.g.

    ```javascript
    const bankAccount = {
      _amount: 1000,
    }
    ```

  * in the above example, it *is* still possible to reassign `_amount`

    * we'll discuss getters and setters next, which are methods designed to respect privacy



#### getters

* ...are methods that get and return the internal properties of an object

* syntax note: in general, getter methods do not need to be called with a set of `()` parentheses

  * syntactically, it looks like we're accessing a property

* e.g.

  ```javascript
  const person = {
    _firstName: 'John',
    _lastName: 'Doe',
    get fullName() {
      if (this._firstName && this._lastName){
        return `${this._firstName} ${this._lastName}`;
      } else {
        return 'Missing a first name or a last name.';
      }
    }
  }
  // To call the getter method: 
  person.fullName; // 'John Doe'
  ```

  

* advantages of getter methods:

  * it's clearer to other developers reading the code what the intention is (as opposed to with the more generic *methods*, which are used for many things)



#### setters

* ...are methods which reassign values of existing properties within an object

* e.g.

  ```javascript
  const person = {
    _age: 37,
    set age(newAge) {
      if (typeof newAge === 'number') {
        this._age = newAge;
      } else {
        console.log('You must assign a number to age');
      }
    }
  };
  person.age = 40;
  console.log(person._age); // Logs: 40
  person.age = '40'; // Logs: You must assign a number to age
  ```

* like getters, setters are called without parentheses

  * syntactically, they look like properties, not methods

* properties may still be assigned without using a setter:

  ```javascript
  person._age = 'forty-five'
  console.log(person._age); // Prints forty-five
  ```

* **important**: notice the syntax for setters:

  * **correct: `object.setter = value;`**
  * incorrect: `object.setter(value);`
    * this is the syntax for a method, not a setter



**important note on getters and setters:**

* they can have the same name!
  * if a value is assigned with the `=`, then the setter is used
  * otherwise, the value is simply returned
* convention seems to be that the property of the object that the getter and setter work on, is the same name, but with a `_` underscore in front of it.



#### factory functions

* are functions that return an object, and are useful for creating many objects quickly

  * parameters may allow the returned object to be customized

* e.g.

  ```javascript
  const robotFactory = (model, mobile) => {
    return {
      model: model,
      mobile: mobile,
      beep () {
        console.log(`Beep Boop`);
      }
    }
  };
  
  const tinCan = robotFactory('P-500', true);
  
  tinCan.beep();
  ```

  

#### property value shorthand

* instead of specifying, as we did above, that the property, `model`, is equal to the value *of the same name*, we can just write:

  ```javascript
  const robotFactory = (model, mobile) => {
    return {
      model,
      mobile,
    }
  };
  ```

  
