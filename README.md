# JS Интенсив
## Занятие 4

__Задание 1__

Массивы в JS являются "неправильными" так как могут хранить в себе данные разных типов и могут изменять свою длину. Массивы совмещают в себе такие структуры данных как стек и очередь, и реализован как частный случай хеш-таблиц.

__Задание 2__

```js
function logger() {
    console.log(`I output only external context: ${this.item}`)
}

const obj = { item: "some value" }

logger.call(obj)

logger.apply(obj)

const bindLogger = logger.bind(obj)
bindLogger()
```

__Бонус. Задание 1__

```js
function bindingFunction(func, thisArg, ...args) {
  const scope = Object.assign({}, thisArg)
  scope._this = func
  return function(...newArgs) {
    scope._this(...args, ...newArgs)
  }
}

function logger() {
    console.log(`I output only external context: ${this.item}`)
}

const obj = { item: "some value" }

const bindLogger = bindingFunction(logger, obj)
bindLogger()
```

