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

```html
<!-- (in index.html) -->
<a-script src="SomeLibrary.js"></a-script>
<a-script src="Main.js"></a-script>
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
```html
<!-- (in index.html) Loads SomeLibrary automatically! -->
<a-script type="module" src="Main.js"></a-script>
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Async Functions & Await
```javascript
// previously
function asyncValue(value, callback) {
  setTimeout(function() {
    callback(value);
  }, 50);
}

(function() {
  asyncValue(42, function(value) {
    assert.equal(42, value);
    done();
  });
})();
```
```javascript
// ES6
function timeout(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}

async function asyncValue(value) {
  await timeout(50);
  return value;
}

(async function() {
  var value = await asyncValue(42);
  assert.equal(42, value);
  done();
})();
```
<!-- .element: class="fragment" data-fragment-index="1" -->

----
## Learn More
* <a href="https://github.com/google/traceur-compiler/wiki/LanguageFeatures">More Features and detail</a>

----
## Cool Stuff! But...
* Can't be used in production! <!-- .element: class="fragment" data-fragment-index="1" -->
* Target ES6 "Release" date: <!-- .element: class="fragment" data-fragment-index="2" --> **December 2014** 
* Old browsers still won't have it! <!-- .element: class="fragment" data-fragment-index="3" -->

----
## What to do?
* Try the <!-- .element: class="fragment" data-fragment-index="1" --> <a href="https://github.com/google/traceur-compiler">Google Traceur Compiler</a>
* Compiles ES6 code into ES5 <!-- .element: class="fragment" data-fragment-index="2" -->
* Online and Offline compilation <!-- .element: class="fragment" data-fragment-index="3" -->
* Subject to many changes, still not good for production! <!-- .element: class="fragment" data-fragment-index="4" -->

====
# Web Components

----
## How current webapps work
* *"Separate Presentation from Business Logic"*
* "Presentation" &rarr; CSS
* "Business Logic" &rarr; JavaScript
* "Structure" &rarr; HTML

----
## How do we organize it?
* JavaScript in RequireJS modules
* HTML in... templates... most of the time? <!-- .element: class="fragment" data-fragment-index="1" -->
* <!-- .element: class="fragment" data-fragment-index="2" --> A few *huge* CSS files
* All entangled and hard to separate <!-- .element: class="fragment" data-fragment-index="3" -->

----
## Reusing HTML/CSS/JS - common questions

&ldquo;What part of the CSS does this HTML need?&rdquo; <!-- .element: class="fragment roll-in" data-fragment-index="1" -->

&ldquo;Where is the behavior for this chunk of HTML?&rdquo; <!-- .element: class="fragment  roll-in" data-fragment-index="2" -->

&ldquo;Does that behavior need other parts of my app to work?&rdquo; <!-- .element: class="fragment roll-in" data-fragment-index="3" -->

&ldquo;Did I import all the correct files for this library?&rdquo; <!-- .element: class="fragment roll-in" data-fragment-index="4" -->

&ldquo;What's the required HTML for this library again?&rdquo; <!-- .element: class="fragment roll-in" data-fragment-index="5" -->

----
# Enter Web Components

----
## Put HTML, CSS, JavaScript all together
* Self contained, encapsulated
* Easily reused
* Can work in isolation
* Import other components in a one-liner
* What about separating presentation and business logic?
  * Each language still has its purpose <!-- .element: class="fragment" data-fragment-index="1" -->
  * Encapsulation and cohesiveness is important <!-- .element: class="fragment" data-fragment-index="2" -->

----
## Using a Popup Library

Messy HTML

```html
<div class="popup-panel">
  <div class="header">
    <h2>Header Content</h2>
    <div class="close-button">X</div>
  </div>
  <p class="content">Some content</p>
</div>
```

With Web Components
```html
<popup closeable="true" header="Header Content">
    Some content
</popup>
```

----
So what * **are** *
## Web Components?

* <a target="_window" href="http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/#toc-separation">Templates</a>
* <a target="_window" href="http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/">Shadow DOM</a>
* <a target="_window" href="http://www.html5rocks.com/en/tutorials/webcomponents/imports/">HTML Imports</a>
* <a target="_window" href="http://www.html5rocks.com/en/tutorials/webcomponents/customelements">Custom Elements</a>

----
## Templates
* Specify blocks of HTML to be used as a template
* Content can't be seen by `querySelector`
* Doesn't execute any scripts inside the HTML

```html
<template id="user-card">
  <a-script>alert("This won't run on load!");</a-script>
  <div>Content, but is hidden from normal DOM</div>
</template>
```

----
## Shadow DOM
* Separate DOM from the main one
* Used for all the presentation-specific HTML
* Prevents accidental overriding of CSS or unintended JavaScript
* Leaves regular DOM nice and clean
* Allow for HTML *encapsulation*

----
## No Shadow DOM

Using `highlight.js` to render code in HTML

```javascript
var fooTheBar = function(bar) {
  return 'foo' + bar;
};
```

view source, and you see this mess:
```html
<code class="javascript"><span class="keyword">var</span> fooTheBar =
  <span class="function">
<span class="keyword">function</span><span class="params">(bar)</span> {</span>
  <span class="keyword">return</span> <span class="string">'foo'</span> + bar;
};</code>
```
<!-- .element: class="fragment roll-in" data-fragment-index="1" -->
----
## With Shadow DOM

View source and see:
```
<code type="javascript">
  var fooTheBar = function(bar) {
    return 'foo' + bar;
  };
</code>
```

All the same markup is still there, just under the covers

----
## HTML Imports
* Lets you fetch an HTML document like we currently do CSS or images
* Can themselves have imports, which are fetched recursively
* Can define styles, templates, etc
* HTML imports become your "dependencies"

```
<link rel="import" href="header.html" id="header-import">
<a-script>
var headerDoc = document.getElementById('header-import').import;
  headerDoc.querySelector('#some-id-in-the-header-file');
</a-script>
```

----
## Custom Elements
* Ties everything together
* Tags can have custom behavior
* Indistinguishable from native elements like `<input>`
* Lifecycle events can control the element
* Events fire when properties change

```javascript
var XFooProto = Object.create(HTMLElement.prototype, {
    bar: {
      get: function() { return 5; }
    },
    foo: {
      value: function() {
        alert('foo() called');
      }
    }
  });

XFooProto.createdCallback = function() {
  this.innerHTML = "<b>Testing 123!</b>";
};

var XFoo = document.registerElement('x-foo', {
  prototype: XFooProto
});
```

----
## A little complicated...

----
<!-- .slide: data-background="no-repeat center url('http://www.polymer-project.org/images/logos/p-logo.svg')" -->
## <a href="http://www.polymer-project.org/">Polymer</a>
* Library putting all these technologies together
* Works as a polyfill for tech until it's a standard
* Library shrinks as more standards are implemented
* Makes these standards easier to use

----
## Polymer Custom Elements
* A layer on top of the standard
* Provides a combined API for web component features
* Templating is built-in, since it's such a common use-case

```
<polymer-element name="x-foo" attributes="bar">
  <style>
    .numbers {
        color: blue;
    }
  </style>
  <template>
    <b>Testing <span class="numbers">123!</span></b>
  </template>
  <a-script>
    Polymer('x-foo', {
      bar: 5,
      foo: function() {
        alert('foo() called');
      }
    });
  </a-script>
</polymer-element>
```
----
## Some neat examples

###<a href="/examples/dismissable">Raw templates and Shadow DOM</a>

###<a href="/examples/github">Polymer "codeless" JSON download</a>

* *Note: * these APIs are evolving
  * Aren't standards yet
  * Polymer is only supported for "evergreen" browsers
  * Might need to enable settings in <code>chrome://flags</code>
    * <a target="_window" href="chrome://flags/#enable-experimental-web-platform-features">Enable experimental Web Platform features</a>
    * <a target="_window" href="chrome://flags/#enable-html-imports">Enable HTML Imports</a>

----
## Wrap Up
* FluentConf was awesome
* New tech is exciting!
* Can't use it in serious apps yet
* But, it's good to be prepared!

### Now <!-- .element: class="fragment" data-fragment-index="1" --> you too can be a **Web Components hipster!** 

----
## Questions?

![hipster with crazy jewelry, yellow sunglasses, a huge beard, cigarette, and suspenders.](img/hipster.jpg "me, before it was cool.")
