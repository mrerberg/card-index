---
tags:
  - programming-patterns
  - asynchronous-programming
---

# Error-first

Паттерн ([[programming-patterns]]) обработки ошибок в асинхронном коде при использовании callback-ов. Договоренность, при которой ошибка передается callback-у первым аргументов.

## Пример

```js
function doSomethingAsync(callback) {
  // Asynchronous operation

  if (isError) {
    callback(new Error('An error occurred'));
  } else {
    callback(null, resultData);
  }
}

doSomethingAsync((err, data) => {
  if (err) {
    console.error('Error:', err.message);
  } else {
    console.log('Data:', data);
  }
});
```

Так же паттерн может принимать следующий вид:
```js
function useCase(dto) {
   // ...
   if(!isValid(dto)) {
     return [new Error('Bad input'), null];
   }
   // ...
   return [null, someValue]
}
```

Или:
```js
function useCase(dto) {
   // ...
   if(!isValid(dto)) {
     return {
        error: new Error('Bad input'),
        result: null,
     };
   }
   // ...
   return {
     error: null,
     result: someValue
   }
}
```