# K&L CSS Style Guide

CSS style guide for all K&amp;L products.

## Table of Contents
1. Spacing
2. Formatting
3. Selectors
4. Naming
5. Sass Features
6. File Organisation

## 1. Spacing
+ Use soft-tabs (spaces) with a four space indent.
+ Put a single space after the `:` in propery declarations.
+ Put a single space before the `{` in rule declarations.
+ Put a single line break between rulesets.
+ When grouping selectors, keep individual selectors to a single line.
+ Place closing braces of declaration blocks on a new line.
+ Include a space after each comma in comma-separated property or function values.

Tip: configure your editor to "show invisibles" or to automatically remove
end-of-line whitespace.

Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to
help maintain the basic whitespace conventions that have been agreed for your
code-base.

## 2. Formatting
+ Use lowercase and shorthand hex color codes `#000` unless using `rgba()`.
+ Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin:
  0px;`.
+ Use single or double quotes consistently. Preference is for single quotes, e.g., content: ''.
+ Order properties within a declaration block alphabetically, for instance
  `margin` goes before `padding`.

## 3. Selectors
+ Only use class names in selectors, no IDs or HTML tag names.
+ Keep selectors to a maximum depth of 2 classes to prevent over-specification.
+ If you need more than 2 classes in a selector, consider specifying a new
  class to cover the edge case.

## 4. Naming
+ Use BEM (Block, Element, Modifier) naming standards for classes. See [CSS
  Wizardry's article](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
  for more information.
  + _Blocks_ represent the top levels of components.
  + _Elements_ represent individual aspects of blocks which contribute to their
    overall appearance/behaviour.
  + _Modifiers_ are different states of a block or element.
+ Use single hyphens as word separators in classes and variables, to match the
  property naming scheme.

## 5. Sass Features
+ Do not use `@extend` unless *absolutely* necessary. It is inefficient and
  generates useless selectors which will never match.
+ Use `@mixin` and `@include` wherever you would use `@extend`. Better to have
  CSS duplication (which is compressable) than selector proliferation.
+ Do not nest declaration blocks. It hides the origin of selectors when
  searching the codebase and can easily result in over-specified selectors
  in the pursuit of pretty code.

## 6. File Organisation
+ Projects must organise their Sass files in the same way. The directory
  structure should be as outlined below.
+ The `assets` folder should ideally appear in the project root.
+ Any directly deployable files (i.e. ones that need no compilation) should
  be stored within the assets folder too. They should be copied out into
  destination folders during build time.

Desired directory structure:
```
/assets
  /sass
    Base path for top-level stylesheets, which largely include partials in the
    directories below.
      /objects
        Generic objects which form building blocks of components. Generally
        focused on layout and visual behaviours.
      /theming
        Application of colours, imagery and so on to objects.
      /components
        Home for styling directives specific to components, i.e. too specific
        to be applied to generic objects.
      /mixins
        Home for mixins.
      /functions
        Home for utility functions.
```
