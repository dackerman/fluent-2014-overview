
# Web Components & The Future of JavaScript Apps
### (A FluentConf overview)

Created by <a href="mailto:dackerman@guidewire.com">David Ackerman (dackerman)</a>

====
# Agenda
* Skim FluentConf themes
* ECMAScript 6
  * What is it?
  * Cool new Features
* Web Components
  * Problems with the current state of web apps
  * How we can address them with Web Components
  * A couple cool demos

====
## FluentConf
### Themes
* New ES6 Features
* Web Components
* Framework Topics (Angular, React, Ember, Meteor, etc)
* Perf/Security Topics
* Focused topics: SVG, D3, Sass
* Handling team dynamics, maintaining code

Note: Listed in descending order of frequency discussed
----
### Links to learn more
* <a target="_window" href="http://fluentconf.com/fluent2014">Main FluentConf site</a>
* <a target="_window" href="http://shop.oreilly.com/product/110000139.do">FluentConf YouTube compilation</a>
* <a target="_window" href="http://fluentconf.com/fluent2014/public/schedule/proceedings">FluentConf Slides</a>

====
# ECMAScript 6 (Harmony)

----
## What is ECMAScript 6?
* New ECMA-262 revision
* Defines "JavaScript" as we know it
* ES6 adds many modern language Features

----
## Cool ECMAScript 6 Features
* Array Comprehensions
* Arrow Functions
* Default Parameters
* Destructuring Assignment
* Iterators & Generators
* Modules
* Async Functions & await

----
## Array Comprehensions
```javascript
// previously
var out = [];
[0, 1, 2].forEach(function(x) {
  [0, 1, 2].forEach(function(y) {
    out.push(x + '' + y);
  });
});

expect(array).to.be.eql([
  '00', '01', '02', '10', '11', '12', '20', '21', '22'
]);```
```javascript
// ES6
var array = [for (x of [0, 1, 2]) for (y of [0, 1, 2]) x + '' + y];

expect(array).to.be.eql([
  '00', '01', '02', '10', '11', '12', '20', '21', '22'
]);
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Arrow Functions
```javascript
// previously
var square = function(x) {
  return x * x;
};```
```javascript
// ES6
var square = (x) => {
  return x * x;
};
var square2 = x => x * x;
```
<!-- .element: class="fragment" data-fragment-index="1" -->

====
# Web Components

----
## Questions?

![hipster with crazy jewelry, yellow sunglasses, a huge beard, cigarette, and suspenders.](img/hipster.jpg "me, before it was cool.")
