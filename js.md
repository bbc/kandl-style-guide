# K&L JavaScript Style Guide

JavaScript style guide for all K&amp;L products.

## Table of Contents

1. [Variables](#variables)
2. [Naming Conventions](#naming-conventions)

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

## Naming Conventions
- Be descriptive when naming things.
```javascript
// bad
var obj = {},
    b = false,
    thing;

// good
var pirateConfigObject = {},
    grogIngredients = ['Kerosene', 'Glycol acid', 'Red dye #2', 'Rum'];
```

- Use camelCase when naming objects, functions, and instances.
```javascript
// bad
var three_headed_monkey = new Monkey(),
    GetButtonText = function () {
        return 'Ask me about Loom';
    },
    RUBBER_TREE;

// good
var threeHeadedMonkey = new Monkey(),
    getButtonText = function () {
        return 'Ask me about Loom';
    },
    rubberTree;
```

- Use PascalCase when naming constructors or classes.
```javascript
// bad
var pirate = function (options) {
    this.name = options.name;
};

var largo = new pirate({
    name: 'Largo LeGrande'
});

// good
var Pirate = function (options) {
    this.name = options.name;
}; 

var largo = new Pirate({
    name: 'Largo LeGrande' 
});
```

**[⬆ back to top](#naming-conventions)**
