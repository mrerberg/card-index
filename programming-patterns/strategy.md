---
tags:
  - programming-patterns
  - design-pattern
  - behavioral-pattern
  - asynchronous-programming
---

# Strategy (Policy)

Паттерн ([[programming-patterns]]), при котором имеется n-ое количество алгоритмов. Алгоритмы выполняют схожую логику и взаимозаменяемы. В зависимости от условия выбирается тот или иной алгоритм.

Для этого необходимо обеспечить:

- совместимость интерфейсов
- совместимость входных и выходных данных

Позволяет выбирать алгоритм в runtime

![[programming-patterns/imgs/strategy.png]]

## Пример

Реализация паттерна. В ассоциативном массиве лежат несколько стратегий, которые выбираются по условию.

```js
// transports/index.js

const transports = {
  // Стратегия
  http: require("./http.js"),
  
  // Стратегия
  ws: require("./ws.js"),
  
  // Стратегия
  fastify: require("./fastify.js"),
};

const transportContext = (transportName) => {
  const server = transports[transportName] || transports.http;

  return server;
};

module.exports = (transport) => transportContext(transport);
```

```js
// main.js

const config = require("./config.js");
const server = require("./transports/index.js")(config.transport);

//...
```

[Больше примеров кода](https://github.com/mrerberg/knowledge-base/tree/main/patterns/strategy)

## Links

- [Стратегия (Strategy) - выбор взаимозаменяемого поведения](https://www.youtube.com/watch?v=hO8VSVv0NqM&list=WL&index=2&t=3s)
- [Wiki](https://en.wikipedia.org/wiki/Strategy_pattern)
- [refactoring.guru](https://refactoring.guru/ru/design-patterns/strategy)
