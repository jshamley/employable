
# JavaScript Tricks

Jeff Shamley | @jeff_shamley

---

# Caveats

---

# IIFE
#### Immediately Invoked Function Expression

```
(function() {
  var vehicle = 'car';
  console.log(vehicle);
  // 'car'
})();
console.log(vehicle);
// Uncaught ReferenceError: vehicle is not defined
```
 <!-- .element: class="fragment" -->
___

# IIFE

```
var vehicle = 'truck';
(function() {
  var vehicle = 'car';
  console.log(vehicle);
  // 'car'
})();
console.log(vehicle);
// 'truck'
```
---

# Block Scope

___
# Block Scope
```
if (true) {
  var vehicle = 'car';
} else {
  var vehicle = 'truck';
}
console.log(vehicle);
// 'car'
```
___
# Block Scope
```
if (true) {
  let vehicle = 'car';
} else {
  let vehicle = 'truck';
}
console.log(vehicle);
// Uncaught ReferenceError: vehicle is not defined
```
```
let vehicle;
if (true) {
  vehicle = 'car';
} else {
  vehicle = 'truck';
}
console.log(vehicle);
// 'car'
```
 <!-- .element: class="fragment" -->
___
# Block Scope
```
if (true) {
  let vehicle = 'car';
  console.log(vehicle);
  // 'car'
} else {
  let vehicle = 'truck';
  console.log(vehicle);
  // 'truck'
}
```
---

# Scope Gotcha

```
for (var i = 0; i < 10; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

```
// 10, 10, 10, 10, 10, 10, 10, 10, 10, 10
```
<!-- .element: class="fragment" -->
___

# Scope Gotcha

```
for (let i = 0; i < 10; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

```
// 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```
<!-- .element: class="fragment" -->
___

# Scope Gotcha

```
for (var i = 0; i < 10; i++) {
  (function () {
    var k = i;
    setTimeout(function() {
      console.log(k);
    }, 1000);
  })();
}
```

```
// 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```
<!-- .element: class="fragment" -->
---

# Use Strict

___
# Use Strict
```
var vehicle;
vehcile = 'car';
console.log(vehicle);
// undefined
console.log(vehcile);
// 'car'
```
___
# Use Strict
```
var vehicle;
(function() {
  vehcile = 'car';
})();
console.log(vehcile);
// 'car'
```
___
# Use Strict
```
'use strict';
var vehicle;
vehcile = 'car';
// Uncaught ReferenceError: vehcile is not defined
```
___
# Use Strict
```
// non-strict code
(function() {
  'use strict';
  // strict code
})();
// non-strict code
```
---

# Double Negation

___
# Double Negation

```
if (obj && obj.someProperty) {
  return true;
} else {
  return false;
}
```
```
return obj && obj.someProperty ? true : false;
```
 <!-- .element: class="fragment" -->
```
return !!obj.someProperty;
```
 <!-- .element: class="fragment" -->
___
# Double Negation

```
const obj = {
  prop: 'testing'
};
const otherObj = {};
const newObj = {
  prop: ''
}
let newestObj;
const hasProp = arg => !!arg.prop;
hasProp(obj); // true
hasProp(otherObj); // false
hasProp(newObj); // false
hasProp(newestObj);
// Uncaught TypeError: Cannot read property 'prop' of undefined
```
---

## Default Variables Values

___
## Default Variable Values
```
let vehicle;
if (!!obj.prop) {
  vehicle = obj.prop;
} else {
  vehicle = 'truck';
}
```
___
## Default Variable Values
```
let car;
let vehicle = car || 'truck';
console.log(vehicle);
// 'truck'
```
___
## Default Argument Values
```
function vehicleType(type = 'truck') {
  return type;
}
vehicleType(null);
// 'truck'
```
```
const vehicleType = (type = 'truck') => type;
vehicleType(null);
// 'truck'
```
<!-- .element: class="fragment" -->
---

## Empty Object Test

```
(Object.keys(obj).length === 0)
```
___

## Object to Array

```
let arr = Object.keys(obj).map(i => {
  // do magic here
  return obj[i];
});
let arr = Object.keys(obj).forEach(i => {
  // do magic here
  return obj[i];
});
let arr = Object.keys(obj).filter(i => {
  // do magic here
  return obj[i].bool === true;
});

```
---

## Converting Variable Types

```
var x = 15;
var y = x + '15';
console.log(y);
// string... '1515'
```
___

## Converting Variable Types

```
var x = '15';
var y = +x;
console.log(y);
// number 15
var z = -x;
console.log(z);
// number -15
```
___

## Converting Variable Types

```
var t = 1;
var f = 0;
!!t
// true
!!f
// false
```
___

## Converting Variable Types

```
var foo = { hello: "world" };
JSON.stringify(foo);
// string '{ "hello":"world" }'
```

```
JSON.stringify(foo, null, 4);
// string
// '{
//    "hello": "world"
// }'
```
<!-- .element: class="fragment" -->
___

## Converting Variable Types

```
var args = { 0: "foo", 1: "bar" };
Array.prototype.slice.call(args)
// [ 'foo', 'bar' ]
```

---

# JavaScript Tricks

## Questions?

Jeff Shamley | @jeff_shamley