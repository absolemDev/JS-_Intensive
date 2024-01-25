# JS Интенсив

## Занятие 3.

__Задание 1__
```js
const counter = {}
```
```js
const counter = new Object()
```
```js
const counter = Object.create(Object.prototype)
```
```js
const counter = Object.assign({}, {})
```
```js
function Counter() {}
const counter = new Counter()
```
```js
class Counter {}
const counter = new Counter()
```

__Задание 2__
```js
const counterCopy = {...counter}
```
```js
const counterCopy = Object.assign({}, counter)
```
```js
const counterCopy = JSON.parse(JSON.stringify(counter))
```
```js
const counterCopy = structuredClone(counter)
```
```js
const counterCopy = _.cloneDeep(counter)
```
```js
const counterCopy = myFunctionForCloningObject(counter)
```

__Задание 3__
```js
function makeCounter() {}
```
```js
const makeCounter = function () {}
```
```js
const makeCounter = function foo() {}
```
```js
const makeCounter = () => {}
```
```js
const makeCounter = (function () {
  return function () {}
})()
```

__Бонус. Задание 1__
```js
const obj1 = { 
  here: {
    is: "on",
    other: "3",
  },
  object: "Y",
}

const obj2 = {
  here: {
    is: "on",
    other: "2",
  },
  object: "Y",
}

function deepEqual(obj1, obj2) {
  let result = true
  for (let key in obj1) {
    result = typeof obj1[key] === "object" ? deepEqual(obj1[key], obj2[key]) : obj1[key] === obj2[key]
    if (!result) break
  }
  return result
}
```

__Бонус. Задание 2__
```js
function reverseStr(str) {
  return Array.from(str).reverse().join("")
}
```
