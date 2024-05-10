##  17. Внесение изменений в коммиты

Цели

Научиться изменять существующие коммиты.
01 Измените страницу, а затем сделайте коммит

Добавьте в страницу комментарий автора.

Файл: hello.html
<!-- Author: Alexander Shvets -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Выполните
git add hello.html
git commit -m "Added copyright statement"
git log
Результат
$ git add hello.html
$ git commit -m "Added copyright statement"
[main e641c0e] Added copyright statement
 1 file changed, 1 insertion(+)
$ git log
e641c0e 2023-11-28 | Added copyright statement (HEAD -> main) [Alexander Shvets]
b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
02 Ой... необходим email

Однако после создания коммита вы понимаете, что любой хороший комментарий должен включать электронную почту автора. Обновите страницу hello.html, включив в нее email.

Файл: hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
03 Измените предыдущий коммит

Мы действительно не хотим создавать отдельный коммит только ради электронной почты. Давайте изменим предыдущий коммит, включив в него адрес электронной почты.

Выполните
git add hello.html
git commit --amend -m "Added copyright statement with email"
Результат
$ git add hello.html
$ git commit --amend -m "Added copyright statement with email"
[main 9288a33] Added copyright statement with email
 Date: Tue Nov 28 05:51:38 2023 -0600
 1 file changed, 1 insertion(+)
04 Просмотр истории

Выполните
git log
Результат
$ git log
9288a33 2023-11-28 | Added copyright statement with email (HEAD -> main) [Alexander Shvets]
b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Мы можем увидеть, что оригинальный коммит «автор» заменен коммитом «автор/email». Этого же эффекта можно достичь путем сброса последнего коммита в ветке, и повторного коммита новых изменений.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book17.md)   [Следующая](./book19.md)