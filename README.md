# JS Интенсив
## Занятие 1. Основы Git

![last](https://github.com/absolemDev/JS_Intensive/assets/118248658/2d4ad26e-5e12-4fa3-a6bf-ef1306b905cf)

![basics](https://github.com/absolemDev/JS_Intensive/assets/118248658/5cc68e69-bd97-4005-b3df-02d4019cbead)

![remote repositories](https://github.com/absolemDev/JS_Intensive/assets/118248658/151da660-04ef-4ed1-9ea3-4dfd59b09e39)

## Занятие 2.

1. Метод HTTP запроса OPTIONS определяет параметры связи, доступные для конкретного ресурса. В ответном сообщении содержит заголовок Allow с перечислением всех поддерживаемых ресурсом методов.

    Можно использовать как ping ресурса.

    Так же используется для предварительных запросов CORS и опирается на три основных заголовка:
   * Access-Control-Request-Method
   * Access-Control-Request-Headers
   * Origin

2. Особенности "HTTP" версии 3.0:
   * В основе лежит технология QUIC, использующая UDP как основной протокола транспортного уровня.
   * Мультиплексирование нескольких потоков в одном соединении.
   * Более гибкий контроль перегрузки, что приводит к повышению пропускной способности трафика.
   * Усовершенствованный механизм восстановления после потерь и прямое исправление ошибок.
   * Процесс установления связи оптимизирован, чтобы избежать избыточного обмена протоколами.
   * Новый механизм сжатия заголовков QPACK, использующий таблицы поиска для кодирования и декодирования заголовков.
   * Улучшенный push. Фрейм PUSH_PROMISE отправляется с сервера через поток запросов, показывающий, что будет содержаться в запросе, на который push будет ответом. Затем он отправляет этот фактический ответ в новом потоке. Отправка сервером может быть ограничена клиентом. Отдельные потоки могут быть отменены с помощью CANCEL_PUSH.

3. Отмена запроса:
   * __XMLHttpRequest__
     ```
     const xhr = new XMLHttpRequest()
     
     xhr.open("GET", "https://...", true)
     xhr.send()
     
     xhr.abort()
     ```
   * __fetch__
     ```
     let controller = new AbortController()
     
     fetch(url, {
         signal: controller.signal
     });

     controller.abort()
     ```
   * __axios__
     ```
     const CancelToken = axios.CancelToken
     const source = CancelToken.source()

     axios.get('/...', {
         cancelToken: source.token
     }).catch(function (thrown) {
         if (axios.isCancel(thrown)) {
             console.log('Request canceled', thrown.message)
         }
     })

     source.cancel()
     ```

4. Создания примитивных значений:
   * __string__
     ```
     const s1 = "строка 1"
     const s2 = 'строка 2'
     const s3 = `строка ${1 + 2}`
     const s4 = Srting("строка " + 4)
     ```
   * __number__
     ```
     const n1 = 1
     const n2 = Number("-2.0")
     ```
   * __boolean__
     ```
     const b1 = true
     const b2 = 1 > 0
     const b3 = Boolean(false)
     ```
   * __null__
     ```
     const n = null
     ```
   * __undefined__
     ```
     const u1
     
     function u2() {
         console.log("undefined")
     }
     u2()
     ```
   * __symbol__
     ```
     const sym1 = Symbol()
     const sym2 = Symbol("sym2")
     ```
   * __bigInt__
     ```
     const bi1 = 1n
     const bi2 = Number("-2")
     ```

5. Переменные, объявленные директивами let и const, переносятся в начало блока. Но если мы сошлёмся в блоке на переменную, до того как она объявлена, то это приведёт к выбросу исключения ReferenceError, потому что переменная находится во "временной мёртвой зоне" с начала блока и до места её объявления.

6. Решeние:
   ```
   const res = "B" + "a" + (1 - "hello")
   console.log(res) // "BaNuN"
   ```
   
   ```
   const res2 = (true && 3) + "d"
   console.log(res2) // "3d"
   ```
   
   ```
   const res3 = Boolean(true && 3) + "d"
   console.log(res3) // "trued"
   ```
    




