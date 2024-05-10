##  19. Переключение веток

Цели

Научиться перемещаться между ветками репозитория.
Теперь в вашем проекте есть две ветки:

Выполните
git log --all
Результат
$ git log --all
9288a33 2023-11-28 | Added copyright statement with email (main) [Alexander Shvets]
903eb1d 2023-11-28 | Included stylesheet into hello.html (HEAD -> style) [Alexander Shvets]
b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
01 Переключение на ветку main

Просто используйте команду git switch для переключения между ветками.

Выполните
git switch main
cat hello.html
Результат
$ git switch main
Switched to branch 'main'
$ cat hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Теперь мы находимся в ветке main. Как видите, в hello.html нет никаких следов style.css. Не волнуйтесь, эти изменения все еще есть в репозитории, но мы не можем увидеть их из ветки main.

02 Вернемся к ветке style

Выполните
git switch style
cat hello.html
Результат
$ git switch style
Switched to branch 'style'
$ cat hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Мы вернулись к ветке style. Как видите, наши изменения, связанные с CSS, присутствуют.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book19.md)   [Следующая](./book21.md)