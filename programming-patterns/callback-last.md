---
tags:
  - programming-patterns
  - asynchronous-programming
---

# Callback-last

Паттерн ([[programming-patterns]]) обработки ошибок в асинхронном коде при использовании callback-ов. Договоренность, при которой ошибка передается callback-у последним аргументом.

Обратный [[error-first]] паттерну.

## Пример

```js
function doSomethingAsync(callback) {
  // Asynchronous operation

  if (isError) {
    callback(null, new Error('An error occurred'));
  } else {
    callback(resultData, null);
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
     return [null, new Error('Bad input')];
   }
   // ...
   return [someValue, null]
}
```
