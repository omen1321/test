##  13. Отмена проиндексированных изменений (перед коммитом)

Цели

Научиться отменять изменения, которые были проиндексированы.
01 Измените файл и проиндексируйте изменения

Внесите изменение в файл hello.html в виде нежелательного комментария

Файл: hello.html
<html>
  <head>
    <!-- This is an unwanted but staged comment -->
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Проиндексируйте это изменение.

Выполните
git add hello.html
02 Проверьте состояние

Проверьте состояние нежелательного изменения.

Выполните
git status
Результат
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   hello.html

Состояние показывает, что изменение было проиндексировано и готово к коммиту.

03 Сбросьте области подготовки

Команда reset сбрасывает область подготовки к HEAD. Это очищает область подготовки от изменений, которые мы только что проиндексировали.

Выполните
git reset HEAD hello.html
Результат
$ git reset HEAD hello.html
Unstaged changes after reset:
M	hello.html
Команда reset (по умолчанию) не изменяет рабочую директорию. Поэтому рабочая директория всё еще содержит нежелательный комментарий. Мы можем использовать команду checkout из предыдущего урока, чтобы убрать нежелательные изменения в рабочей директории.

04 Переключитесь на версию коммита

Выполните
git checkout hello.html
git status
Результат
$ git checkout hello.html
Updated 1 path from the index
$ git status
On branch main
nothing to commit, working tree clean
Наша рабочая директория опять чиста.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book13.md)   [Следующая](./book15.md)