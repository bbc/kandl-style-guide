# K&L JavaScript Style Guide

JavaScript style guide for all K&amp;L products.

## Table of Contents

1. [Variables](#variables)
1. [Whitespace](#whitespace)
1. [Naming Conventions](#naming-conventions)
1. [Strings](#strings)
1. [Semicolons](#semicolons)
1. [Conditional Expressions & Equality](#conditional-expressions--equality)
1. [Blocks](#blocks)
1. [Functions](#functions)
1. [Properties](#properties)
1. [Comments](#comments)
1. [License](#license)

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

- Declare unassigned variables last.
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

- Add an empty line after variable declarations
```javascript
// bad
var guybrush = new Pirate();
guybrush.sayHello();

// good
var guybrush = new Pirate();

guybrush.sayHello()
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

- Use indentation when making method chains. Use a leading dot, which
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

- Strings longer than 100 characters should be written across multiple lines using string concatenation.
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

## Conditional Expressions & Equality

- Use `===` and `!==` over `==` and `!=`.
- Conditional expressions are evaluated using coercion with the `ToBoolean` method and always follow these simple rules:

+ **Objects** evaluate to **true**
+ **Undefined** evaluates to **false**
+ **Null** evaluates to **false**
+ **Booleans** evaluate to **the value of the boolean**
+ **Numbers** evaluate to **false** if **+0, -0, or NaN**, otherwise **true**
+ **Strings** evaluate to **false** if an empty string `''`, otherwise **true**

```javascript
if ([0]) {
    // true
    // An array is an object, objects evaluate to true
}
```

- Use shortcuts.

```javascript
// bad
if (name !== '') {
    console.log('Hi ' + name);
}

// good
if (name) {
    console.log('Hi ' + name);
}

// bad
if (collection.length > 0) {
    console.log('The collection has content.');
}

// good
if (collection.length) {
    console.log('The collection has content.');
}
```

- For more information see [Truth Equality and JavaScript](http://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108) by Angus Croll.

**[⬆ back to top](#table-of-contents)**


## Blocks

- Use braces with all multi-line blocks.

```javascript
// bad
if (test)
    return false;

// good
if (test) return false;

// good
if (test) {
    return false;
}

// bad
var getName = function () { return 'Bobbin Threadbare'; };

// good
var getName = function () {
    return 'Bobbin Threadbare';
};
```

**[⬆ back to top](#table-of-contents)**

## Functions
  - Always use function expressions rather than function declarations. This enforces better order in your code.
```javascript
// bad
function whereDoesItBelong () {
    console.log('In a museum!');
}

// good
var anonymous = function () {
    return true;
};

// good
var named = function named () {
    return true;
};

// good
(function () {
    console.log('It belongs in a museum!');
})();
```

- Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears.
- **Note:** ECMA-262 defines a `block` as a list of statements. A function declaration is not a statement. [Read ECMA-262's note on this issue](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf#page=97).
```javascript
// bad
if (currentUser === 'Roger') {
    function sayHelloRoger() {
        console.log('Hello Roger.');
    }
}

// good
var sayHelloRoger;

if (currentUser === 'Roger') {
    sayHelloRoger = function sayHelloRoger () {
        console.log('Hello Roger.');
    };
}
```
**[⬆ back to top](#table-of-contents)**

## Properties
  - Use dot notation when accessing properties.

    ```javascript
    var reginaldBlackbeard = {
        pirate: true,
        age: 39,
        favouritePlace: 'Library'
    };

    // bad
    var isPirate = reginaldBlackbeard['pirate'];

    // good
    var isPirate = reginaldBlackbeard.pirate;
    ```

  - Use subscript notation `[]` when accessing properties with a variable.

    ```javascript
    var reginaldBlackbeard = {
        pirate: true,
        age: 39,
        favouritePlace: 'Library'
    };

    var getProp = function (prop) {
      return reginaldblackbeard[prop];
    }

    var isPirate = getProp('pirate');
    ```

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


## License

This Style Guide is based on Airbnb's excellent [JavaScript Style Guide](https://github.com/airbnb/javascript) released under the MIT License. The license has been preserved below. Any modifications made to this document are also released under the MIT License.

(The MIT License)

Copyright (c) 2014 Airbnb

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[⬆ back to top](#table-of-contents)**
