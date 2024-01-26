# JS Интенсив
## Занятие 4

```js
function bindingFunction(func, thisArg, ...args) {
  const scope = Object.assign({}, thisArg)
  scope._this = func
  return function(...newArgs) {
    scope._this(...args, ...newArgs)
  }
}

function logger(a) {
    console.log(`I output only external context: ${this.item}`);
}

const obj = { item: "some value" }

const bindLogger = bindingFunction(logger, obj)

bindLogger()
```

