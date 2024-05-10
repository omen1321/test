##  12. Отмена локальных изменений (до индексации)

Цели

Научиться отменять изменения в рабочей директории.
01 Переключитесь на ветку main

Убедитесь, что вы находитесь на последнем коммите ветки main, прежде чем продолжить работу.

Выполните
git switch main
02 Измените hello.html

Иногда после того как вы изменили файл в рабочей директории, вы передумали и хотите просто вернуться к тому, что уже было закоммичено. Команда checkout справится с этой задачей.

Внесите изменение в файл hello.html в виде нежелательного комментария.

Файл: hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is a bad comment. We want to revert it. -->
  </body>
</html>
03 Проверьте состояние

Сначала проверьте состояние рабочей директории.

Выполните
git status
Результат
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   hello.html

no changes added to commit (use "git add" and/or "git commit -a")
Мы видим, что файл hello.html был изменен, но еще не проиндексирован.

04 Отмена изменений в рабочем каталоге

Используйте команду checkout для переключения в версию файла hello.html в репозитории.

Выполните
git checkout hello.html
git status
cat hello.html
Результат
$ git checkout hello.html
Updated 1 path from the index
$ git status
On branch main
nothing to commit, working tree clean
$ cat hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Команда status показывает нам, что в рабочей директории не было сделано никаких незафиксированных изменений. И «нежелательный комментарий» больше не является частью содержимого файла.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book12.md)   [Следующая](./book14.md)