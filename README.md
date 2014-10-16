# K&L CSS Style Guide

CSS style guide for all K&amp;L products.

## Table of Contents
1. Spacing
2. Formatting

## Spacing
+ Use soft-tabs (spaces) with a two space indent.
+ Put a single space after the `:` in propery declarations.
+ Put a single space before the `{` in rule declarations.
+ Put a single line break between rulesets.
+ When grouping selectors, keep individual selectors to a single line.
+ Place closing braces of declaration blocks on a new line.

## Formatting
+ Use hex color codes `#000` unless using `rgba()`.
+ Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin:
  0px;`.
* Order properties within a declaration block alphabetically, for instance 
  `margin` goes before `padding`.

## Selectors
* Only use class names in selectors, no IDs or HTML tag names.
* Keep selectors to a maximum depth of 2 classes to prevent over-specification.
* If you need more than 2 classes in a selector, consider specifying a new
  class to cover the edge case.

## Class Naming
* Use BEM (Block, Element, Modifier) naming standards for classes. See [CSS 
  Wizardry's article](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
  for more information.
  * *Blocks* represent the top levels of components.
  * *Elements* represent individual aspects of blocks which contribute to their
    overall appearance/behaviour.
  * *Modifiers* are different states of a block or element.

