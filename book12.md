##  11. Создание тегов версий

Цели

Узнать, как создавать теги для коммитов для использования в будущем.
Думаю, вы согласитесь, что работать с хешами коммитов напрямую просто неудобно. Разве не было бы здорово, если бы вы могли обозначать конкретные коммиты понятными для человека названиями? Таким образом, вы могли бы четко видеть важные вехи в истории проекта. Кроме того, вы могли бы легко перейти к определенной версии проекта по ее названию. Именно для этого в Git придумали теги.

Давайте назовем текущую версию страницы hello.html первой, то есть v1.

01 Создайте тег первой версии

Выполните
git tag v1
git log
Результат
$ git tag v1
$ git log
b7614c1 2023-11-28 | Added HTML header (HEAD -> main, tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Теперь текущая версия страницы называется v1.

02 Теги для предыдущих версий

Обозначим версию, предшествующую текущей, названием v1-beta. Прежде всего, мы переключимся на предыдущую версию. Вместо того чтобы искать хеш коммита, мы будем использовать обозначение ^, а именно v1^, указывающее на коммит, предшествующий v1.

Если обозначение v1^ вызывает у вас какие-то проблемы, попробуйте также v1~1, указывающее на ту же версию. Это обозначение можно определить как «первую версию, предшествующую v1».
Выполните
git checkout v1^
cat hello.html
Результат
$ git checkout v1^
Note: switching to 'v1^'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 46afaff Added standard HTML page tags
$ cat hello.html
<html>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
Это версия с тегами <html> и <body>, но еще пока без <head>. Давайте сделаем ее версией v1-beta.

Выполните
git tag v1-beta
git log
Результат
$ git tag v1-beta
$ git log
46afaff 2023-11-28 | Added standard HTML page tags (HEAD, tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
03 Переключение по имени тега

Теперь попробуйте попереключаться между двумя отмеченными версиями.

Выполните
git checkout v1
git checkout v1-beta
Результат
$ git checkout v1
Previous HEAD position was 46afaff Added standard HTML page tags
HEAD is now at b7614c1 Added HTML header
$ git checkout v1-beta
Previous HEAD position was b7614c1 Added HTML header
HEAD is now at 46afaff Added standard HTML page tags
04 Просмотр тегов с помощью команды tag

Вы можете увидеть, какие теги доступны, используя команду git tag.

Выполните
git tag
Результат
$ git tag
v1
v1-beta
05 Просмотр Тегов в логах

Вы также можете посмотреть теги в логе.

Выполните
git log main --all
Результат
$ git log main --all
b7614c1 2023-11-28 | Added HTML header (tag: v1, main) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (HEAD, tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
Вы можете видеть теги (v1 и v1-beta) в логе вместе с именем ветки (main). Кроме того, метка HEAD показывает коммит, на который вы переключились (на данный момент это v1-beta).
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book11.md)   [Следующая](./book13.md)