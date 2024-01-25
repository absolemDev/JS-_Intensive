# JS Интенсив
## Занятие 1. Основы Git

![last](https://github.com/absolemDev/JS_Intensive/assets/118248658/2d4ad26e-5e12-4fa3-a6bf-ef1306b905cf)

![basics](https://github.com/absolemDev/JS_Intensive/assets/118248658/5cc68e69-bd97-4005-b3df-02d4019cbead)

![remote repositories](https://github.com/absolemDev/JS_Intensive/assets/118248658/151da660-04ef-4ed1-9ea3-4dfd59b09e39)

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
  return str.split("").reverse().join("")
}
```
