---
tags: 
  - nodejs
---

# How works

[[node-js]]

К примеру, мы вызываем некое апи. Пусть будет readFile.

![how-works-1](how-works-1.png)

Мы передаем callback в функцию readFile. Переданный callback далее попадает в Node standard library API

![how-works-2](how-works-2.png)

Библиотеке может понадобится thread pull для осуществления внешней операции (доступ к файлам, сети).

![how-works-3](how-works-3.png)

Когда библиотека понимает, что результат нужно передать в callback, то callback помещается в callback queue.

![how-works-4](how-works-4.png)

Далее Event Loop подхватывает callback и кидает его на stack вызовов в приложении.

![how-works-5](how-works-5.png)

Если нет на очереди callback-ов, нет задач для выполнения, то происходит завершение выполнения, выход.

## Links

- <https://www.youtube.com/watch?v=mRvzgBGLVyM&t=125s>
