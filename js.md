# K&L JavaScript Style Guide

JavaScript style guide for all K&amp;L products.

## Table of Contents

1. [Variables](#variables)
1. [Whitespace](#whitespace)
1. [Naming Conventions](#naming-conventions)
1. [Strings](#strings)
1. [Semicolons](#semicolons)
1. [Functions](#functions)
1. [Comments](#comments)

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

## Whitespace
- Use soft tabs set to 4 spaces.
```javascript
// bad
var getPlantName() {
∙∙return 'Chuck the Plant';
}

// good
var getPlantName() {
∙∙∙∙return 'Chuck the Plant';
}
```

- Place 1 space after the `function` keyword and 1 space before the leading brace.
```javascript
// bad
var setButtonText = function(){
    var buttonText = 'Ask me about Grim Fandango.';
};

// good
var setButtonText = function () {
    var buttonText = 'Ask me about Grim Fandango.';
};

// bad
person.set('attr',{
    name: 'Guybrush',
    talent: 'Can hold breath for 10 minutes'
});

// good
person.set('attr', {
    name: 'Guybrush',
    talent: 'Can hold breath for 10 minutes'
});
```

- Set off operators with spaces.
```javascript
// bad
var x=y+5;

// good
var x = y + 5;
```

- Use indentation when making long method chains. Use a leading dot, which
  emphasizes that the line is a method call, not a new statement.
```javascript
// bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

// bad
$('#items').
  find('selected').
    highlight().
    end().
  find('.open').
    updateCount();

// good
$('#items')
  .find('.selected')
    .highlight()
    .end()
  .find('.open')
    .updateCount();

// bad
var leds = stage.selectAll('.led').data(data).enter().append('svg:svg').class('led', true)
    .attr('width',  (radius + margin) * 2).append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);

// good
var leds = stage.selectAll('.led')
    .data(data)
  .enter().append('svg:svg')
    .class('led', true)
    .attr('width',  (radius + margin) * 2)
  .append('svg:g')
    .attr('transform', 'translate(' + (radius + margin) + ',' + (radius + margin) + ')')
    .call(tron.led);
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
**[⬆ back to top](#table-of-contents)**

## Strings
- Use single quotes `''` for strings.
```javascript
// bad
var name = "Murray";

// good
var name = 'Murray';

// bad
var fullName = "Murray " + this.lastName;

// good
var fullName = 'Murray ' + this.lastName;
```

- Strings longer than 80 characters should be written across multiple lines using string concatenation.
```javascript
// bad
var errorMessage = 'If a woodchuck could chuck and would chuck some amount of wood, what amount of wood would a woodchuck chuck?';

// bad
var errorMessage = 'If a woodchuck could chuck and would chuck some amount ' +
'of wood, what amount of wood would a woodchuck chuck? Even if a woodchuck ' +
'could chuck wood and even if a woodchuck would chuck wood, should a ' +
'woodchuck chuck wood?';

// good
var errorMessage = 'If a woodchuck could chuck and would chuck some amount ' +
    'of wood, what amount of wood would a woodchuck chuck? Even if a woodchuck ' +
    'could chuck wood and even if a woodchuck would chuck wood, should a ' +
    'woodchuck chuck wood?';
```

**[⬆ back to top](#table-of-contents)**

## Semicolons
- Yes please.
```javascript
// bad
(function () {
    var name = 'Thriftweed'
    return name
})()

// good
(function () {
    var name = 'Thriftweed';
    return name;
})();

// good (guards against the function becoming an argument when two files with IIFEs are concatenated)
;(function () {
    var name = 'Thriftweed';
    return name;
})();
```
**[⬆ back to top](#table-of-contents)**

## Functions
**[⬆ back to top](#table-of-contents)**

## Comments
Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment.
```javascript
// bad
var fettuciniBrothers = ['Bill', 'Alfredo']; // Names of the Fettucini Brothers.

// good
// Names of the Fettucini Brothers.
var fettuciniBrothers = ['Bill', 'Alfredo']; 

// bad
var getNamesOfFettuciniBrothers = function () {
    var fettuciniBrothers = ['Bill', 'Alfredo']; 
    // Return names of the Fettucini Brothers.
    return fettuciniBrothers;
};

// good
var getNamesOfFettuciniBrothers = function () {
    var fettuciniBrothers = ['Bill', 'Alfredo']; 

    // Return names of the Fettucini Brothers.
    return fettuciniBrothers;
};
```

- Use `/** ... */` for multiline comments. Include a description, specify types and values for all parameters and return values.
```javascript
// bad
// Takes a user's name, says hello and
// tries to sell them a leather jacket.
var sayHello = function (name) {
    return 'Hi ' + name + ', I\'m selling these fine leather jackets.';
};

// good
/**
 * Takes a user's name, says hello and
 * tries to sell them a leather jacket.
 *
 * @param {String} name Name of person being spoken to.
 * @param {String} Sentence to be spoken.
 */
```
**[⬆ back to top](#table-of-contents)**
