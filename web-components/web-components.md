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

----
## Default Parameters
```javascript
// previously
function f(list, indexA, indexB) {
  if (typeof indexA === 'undefined') indexA = 0;
  if (typeof indexB === 'undefined') indexB = list.length;
  return [list, indexA, indexB];
}```
```javascript
// ES6
function f(list, indexA = 0, indexB = list.length) {
  return [list, indexA, indexB];
}
expect(f([1,2,3])).to.be.eql([[1,2,3], 0, 3]);
expect(f([1,2,3], 1)).to.be.eql([[1,2,3], 1, 3]);
expect(f([1,2,3], 1, 2)).to.be.eql([[1,2,3], 1, 2]);
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Destructuring Assignment
```javascript
// previously
var aPoint = {x: 123, y: 456};
var x = aPoint.x;
var y = aPoint.y;

var rect = {topLeft: {x: 1, y: 2}, bottomRight: {x: 3, y: 4}};
var x1 = rect.topLeft.x;
var y1 = rect.topLeft.y;
var x2 = rect.bottomRight.x;
var y2 = rect.bottomRight.y;
```
```javascript
// ES6
var aPoint = {x: 123, y: 456};
var {x, y} = aPoint;

var rect = {topLeft: {x: 1, y: 2}, bottomRight: {x: 3, y: 4}};
var {topLeft: {x: x1, y: y1}, bottomRight: {x: x2, y: y2}} = rect;
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Iterators & Generators
```javascript
// previously
...?
```
```javascript
// ES6
function* intsBetween(min, max) {des
  for (var i = min; i < max; i++) {
    yield i;
  }
}

var result = [];
for (let value of intsBetween(4, 10)) {
  result.push(value);
}
expect(result).toEqual([4, 5, 6, 7, 8, 9, 10]);
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Modules
```javascript
// previously
// (SomeLibrary.js)
var SomeLibrary = (function() {
  var internalVar = 'a';

  return {
    externalVar: internalVar + 'b';
  };
})();

// (Main.js)
expect(SomeLibrary.externalVar).toBe('ab');
```

```
<!-- (in index.html) -->
&lt;script src="SomeLibrary.js"&gt;</script>
<script src="Main.js"&gt;&lt;/script&gt;
```
```javascript
// ES6
// (SomeLibrary.js)
var internalVar = 'a';
export var externalVar = internalVar + 'b';

// (Main.js)
import {externalVar} from './SomeLibrary';

expect(externalVar).toBe('ab');
```
```xhtml
&lt;!-- (in index.html) Loads SomeLibrary automatically! --&gt;
&lt;script type="module" src="Main.js"&gt;&lt;/script&gt;
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Title
```javascript

```
```javascript

```
<!-- .element: class="fragment" data-fragment-index="1" -->

====
# Web Components

----
## Questions?

![hipster with crazy jewelry, yellow sunglasses, a huge beard, cigarette, and suspenders.](img/hipster.jpg "me, before it was cool.")
