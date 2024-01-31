# JS Интенсив
## Занятие 5.

__Задание 1__

Алгоритмы сортировок:
* __Пузырьковая сортировка (Bubble sort)__
  
  Берутся два первых элемента массива, сравниваются и расставляются по порядку. Затем происходит смещение на один элемент вправо и сравниваются уже второй и третий элементы. И так далее до конца массива.
* __Сортировка выбором (Selection sort)__
  
  Начинается с первого элемента массива и движется направо. Сравниваются элементы попарно и отбирается минимальный из них. Найденный минимум меняется местами с первым не отсортированным элементом в начале массива.
* __Сортировка вставками (Insertion sort)__
  
  Полагается, что начало массива уже отсортировано (изначально 1 элемент). Берется первый неотсортированный элемент (индекс 1) и последовательно сравнивает его с отсортированными, находя нужное место. После этого длина отсортированной части увеличивается (теперь уже два отсортированных элемента), далее берется следующий элемент (индекс 2).
* __Сортировка слиянием (Merge sort)__
  
  Исходный массив разделяется на две примерно равные части. Каждая часть сортируется отдельно. Обе отсортированные части объединяются в один массив.
* __Быстрая сортировка (Quick sort)__
  
  Ввыбирается опорный элемент, относительно которого будет происходит сортировка. Равные и большие элементы помещаются справа, меньшие – слева. Затем к полученным подмассивам рекурсивно применяются два первых пункта.

__Задание 2__

Операторы – это специальные символы, которые используются для выполнения различных операций. В JavaScript существуют унарными (работать с одним операндом), бинарные (работать с двумя операндами) или тернарные (работать с тремя операндами).

Выражения в JavaScript используются для получения значений или выполнения вычислений. Они могут состоять из переменных, литералов, функций, операторов и других элементов. Выражения оцениваются в значение, которое может быть использовано в коде.

Циклы:
* for (инициализация; условие; инкремент): используется для выполнения блока кода определенное количество раз.
* while (условие): продолжает выполнять блок кода, пока условие истинно.
* do…while (условие): сначала выполняет блок кода, затем проверяет условие.
* for…in (переменная in объект): перебирает свойства объекта.
* for…of (переменная of итерируемый объект): перебирает значения итерируемого объекта.

__Задание 3__

```js
// создание объекта person - литеральный способ
const person = {
  firstName: "Илья",
  lastName: "Фролов",
  getFullName: function() {
    return `${this.lastName} ${this.firstName}`
  },
}

// создание объекта person - конструктор
const person = new Object({
  firstName: "Илья",
  lastName: "Фролов",
  getFullName: function() {
    return `${this.lastName} ${this.firstName}`
  },
})

// создание объекта person - класс
class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName,
    this.lastName = lastName,
  }

  getFullName() {
    return `${this.lastName} ${this.firstName}`
  }
}
const person = new Person("Илья", "Фролов");

// создание объекта person2 - литеральный способ
const person2 = {
  firstName: "Эл",
  lastName: "Фрол",
  __proto__: person,
}

// создание объекта person2 - метод Object.create
const person2 = Object.create(person, {
  firstName: {value: "Эл", enumerable: true, writable: true, configurable: true},
  lastName: {value: "Фрол", enumerable: true, writable: true, configurable: true},
});

// метод getFullName доступен в person2
console.log(person2.getFullName()) // Фрол Эл

// метод logInfo будет доступен объекту person и его наследникам
person.logInfo = function() {
  console.log(`Имя: ${this.firstName}. Фамилия: ${this.lastName}.`);
}

// определение метода logInfo с помощью метода defineProperty
Object.defineProperty(person, 'logInfo', {
  value: function() {
    console.log(`Имя: ${this.firstName}. Фамилия: ${this.lastName}.`);
  },
  configurable: true,
});

// метод logInfo будет доступен всем объектам
Object.prototype.logInfo = function() {
  console.log(`Имя: ${this.firstName}. Фамилия: ${this.lastName}.`);
}

person.logInfo(); // Имя: Илья. Фамилия: Фролов.
person2.logInfo(); // Имя: Эл. Фамилия: Фрол.
```

__Задание 4__

```js
class Person {
  constructor(firstName, lastName) {
    this._firstName = firstName;
    this._lastName = lastName;
  }

  getFullName() {
    return `${this._lastName} ${this._firstName}`
  }
}

class PersonThree extends Person {
  constructor(firstName, lastName) {
    super(firstName, lastName);
  }
  
  get name() {
    return this._firstName;
  }

  set name(value) {
    this._name = _firstName;
  }
}
```

__Бонус. Задание 1__

```js
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
total = 13;

const firstSum = (arr, total) => {
  for (let i = 0; i < arr.length - 2; i++) {
    let start = i + 1
    let end = arr.length - 1
    while (start <= end) {
      const mid = Math.round((end - start) / 2) + start
      if (arr[i] + arr[mid] === total) return [arr[i], arr[mid]]
      if (arr[i] + arr[mid] < total) {
        start = mid
      } else {
        end = mid
      }
      if (start === end) break
    }
  }
  return "No such sum"
}

console.log(firstSum(arr,total)) //result = [4, 9]
```

__Бонус. Задание 2__

Сложность алгоритма `O((n - 1) * log(n))`
