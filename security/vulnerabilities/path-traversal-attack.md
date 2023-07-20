# Path traversal attack

Суть атаки заключает в том, что злоумышленник пытается получить доступ до различных файлов в каталоге через перебор путей посредством **dot-dot-slash (../)**. Соответственно, у него не должно быть доступа.

## Пример

```text
http://some_site.com.br/get-files.jsp?file=report.pdf
```

"Зараженный" url

```text
http://some_site.com.br/get-files?file=../../../../some dir/some file
```

## Links

- https://github.com/HowProgrammingWorks/NodeServer/blob/master/native-2022/main.mjs#L27
  Обращаться к серверу нужно через http-клиент, браузер будет автоматически обрезать символы (../../), не давая произвести атаку