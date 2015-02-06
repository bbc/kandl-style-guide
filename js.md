# K&L JavaScript Style Guide

JavaScript style guide for all K&amp;L products.

## Table of Contents

1. [Variables](#variables)

## Variables
- Should always be declared to prevent polluting the global namespace.
```javascript
// bad
guybrush = new Pirate();

// good
var guybrush = new Pirate();
```

- Should use one `var` keyword and commas when declaring multiple variables. This makes them easier to read.
```javascript
// bad
var guybrush = new Pirate();
var leChuck = new Pirate();
var grog = true;

// good
var guybrush = new Pirate(),
    leChuck = new Pirate(),
    grog = true;
```

- Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.
```javascript
// bad
var grog,
    guybrush = new Pirate(),
    leChuck = new Pirate();

// good
var guybrush = new Pirate(),
    leChuck = new Pirate(),
    grog;
```

- Assign variables at the top of their scope. This helps avoid issues with variable declaration and hoisting related issues.
```javascript
// bad
var sayHello = function () {
   openMouth();

   var sentence = 'I\'m Guybrush Threepwood, mighty pirate.';
};

// good
var sayHello = function () {
   var sentence = 'I\'m Guybrush Threepwood, mighty pirate.';

   openMouth();
};
```

**[⬆ back to top](#table-of-contents)**
