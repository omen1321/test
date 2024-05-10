##  10. Получение старых версий

Цели

Научиться возвращать рабочую директорию к любому предыдущему состоянию.
Git позволяет очень просто путешествовать во времени, по крайней мере, для вашего проекта. Команда checkout обновит вашу рабочую директорию до любого предыдущего коммита.

01 Получите хеши предыдущих коммитов

Выполните
git log
Результат
$ git log
b7614c1 2023-11-28 | Added HTML header (HEAD -> main) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Просмотрите историю изменений и найдите хеш первого коммита. Он должен быть в последней строке результата git log. Используйте этот хеш (достаточно первых 7 символов) в команде ниже. Затем проверьте содержимое файла hello.html.

Выполните
git checkout <hash>
cat hello.html
Многие команды Git принимают хеши коммитов в качестве аргументов. Хеши коммитов будут отличаться в разных репозиториях, поэтому когда вы видите, что в команде есть пометка <hash>, то это значит, что вам надо подставить вместо нее реальный хеш из вашего репозитория.
Вы увидите:

Результат
$ git checkout 5836970
Note: switching to '5836970'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 5836970 Initial commit
$ cat hello.html
Hello, World!
Обратите внимание, что сейчас содержимое файла hello.html — это тот самый текст, с которого мы начинали.

02 Вернитесь к последней версии в ветке main

Чтобы вернуться к последней версии нашего кода, нам нужно переключиться на ветку по умолчанию, main. Для переключения между ветками можно воспользоваться командойswitch.

Команда checkout в течение длительного времени была своеобразным швейцарским ножом в мире Git. Она имеет множество различных опций, которые позволяют выполнять совершенно разные вещи: переключать ветки, сбрасывать код и так далее. В какой-то момент команда Git решила разделить ее на несколько команд. Командаswitch является одной из них — ее единственным назначением является переключение между ветками. Команда checkout все еще доступна, но использовать ее для переключения веток больше не рекомендуется.
Выполните
git switch main
cat hello.html
Вы увидите:

Результат
$ git switch main
Previous HEAD position was 5836970 Initial commit
Switched to branch 'main'
$ cat hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
main — имя ветки по умолчанию. Переключаясь на ветку, вы попадаете на её последнюю версию.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book10.md)   [Следующая](./book12.md)