# JS Интенсив
## Занятие 6.

__Задание 1__

```js
let promiseTwo = new Promise((resolve, reject) => {
   resolve("a");
});

promiseTwo
.then((res) => {
   return res + "b";
})
.then((res) => {
   return res + "с";
})
.finally((res) => {
   return res + "!!!!!!!";
})
.catch((res) => {
   return res + "d";
})
.then((res) => {
   console.log(res); // "abc"
});
```

__Задание 2__

```js
function doSmth() {
   return Promise.resolve("123");
}

doSmth()
.then(function (a) {
   console.log("1", a); // "1 123"
   return a;
})
.then(function (b) {
   console.log("2", b); // "2 123"
   return Promise.reject("321");
})
.catch(function (err) {
   console.log("3", err); // "3 321"
})
.then(function (c) {
  console.log("4", c); // "4 undefined"
  return c; // undefined
});
```

__Задание 3__

```js
const numbers = [10, 12, 15, 21]

const timeoutLog = (arr) => {
  for (let i = 0; i < arr.length; i++) {
    setTimeout(() => console.log(`${i}: ${arr[i]}`), 3000 * (i + 1))
  }
}

timeoutLog(numbers)
```

__Задание 4__

Top Level Await позволяет выполнять асинхронные операции на самом верхнем уровне кода, до того как будет запущен основной цикл событий.
* Можно использовать оператор await прямо в начале кода, перед тем как начнется выполнение программы.
* Когда используется await, программа приостанавливает свое выполнение и ждет, пока асинхронная операция завершится.
* После того как операция завершилась, программа продолжает свое выполнение с места, где была вызвана функция.

__Бонус. Задание 1__

```js
async function fetchUrl(url) {
  for (let tryCount = 1; tryCount <= 5; tryCount++) {
    try {
      const response = await fetch(url);
      const result = await response.json();
      return result;
    } catch (err) {
      if (tryCount < 5) continue
      throw new Error(err)
    }
  }
}
```
