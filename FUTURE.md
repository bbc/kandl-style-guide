# Education CSS Style Guide
# Future Plans

The style guide will continue to evolve over time, this document serves
as an early staging post for ideas which are being shaped to appear in
the future.

## Documentation
Documenting Sass mixins and functions is possible, and the best tool out there
to do it appears to be SassDoc. We should do this, in a minimal style, so that
complex areas of our Sass framework are made a little easier to understand and
maintain.

The benefits are to be found once combined with automatic API documentation for
our existing codebase, such as JavaScript and PHP.

## OOCSS
Object Oriented CSS is the "next big thing" in the CSS world. A few people are
advocating for it, and experiments have been performed on some Education code to
judge the benefits and feasibility of doing it.

In the future, we may well want to adopt this approach to building our Sass.
Before that, we need to really understand what it is (as the current thinking
around it is a little fluffy) and how to "codify" it best in a style guide.

## Modularisation
At the moment our Sass is rather disorganised. We have a dumping ground
(kandl-common-sass), a bunch of modules, and our applications. We should find
a standard of organising our Sass code so that moving between products or
shared modules isn't a learning exercise each time.

## Naming schemes
Naming classes is a little haphazard - different products have different styles
for namespacing classes to themselves, and we have to ensure we don't collide
with other BBC modules and each other. Additionally, we don't really denote
classes which are used purely for feature detection or interaction.

We should come up with a naming scheme which solves this issue, and can be
followed across our entire codebase.
