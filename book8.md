##  7. Коммит изменений

Цели

Научиться коммитить изменения в репозиторий.
01 Закоммитьте изменения

Достаточно об индексации. Давайте сделаем коммит того, что мы проиндексировали, в репозиторий.

Когда вы ранее использовали git commit для коммита первоначальной версии файла hello.html в репозиторий, вы включили метку -m, которая делает комментарий в командной строке. Команда commit позволит вам интерактивно редактировать комментарии для коммита. Теперь давайте это проверим.

Если вы опустите метку -m из командной строки, Git перенесет вас в редактор по вашему выбору. Редактор выбирается из следующего списка (в порядке приоритета):

переменная среды GIT_EDITOR
параметр конфигурации core.editor
переменная среды VISUAL
переменная среды EDITOR
У меня переменная EDITOR установлена в vim. Если вы предпочитаете GUI-редактор, то теперь можно использовать VS Code в качестве Git-редактора.
Сделайте коммит сейчас и проверьте состояние.

Выполните
git commit
Вы увидите в вашем редакторе:

Результат
|
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch main
# Changes to be committed:
#       modified:   hello.html
#
В первой строке введите комментарий: Added h1 tag. Сохраните файл и выйдите из редактора (для этого в редакторе по умолчанию (Vim) вам нужно нажать клавишу ESC, ввести :wq и нажать Enter). Вы увидите:

Результат
$ git commit
[main 78433de] Added h1 tag
 1 file changed, 1 insertion(+), 1 deletion(-)
Строка «Waiting for Emacs...» получена из программы emacsclient, которая посылает файл в запущенную программу emacs и ждет его закрытия. Остальные выходные данные – стандартные коммит-сообщения.

02 Проверьте состояние

В конце давайте еще раз проверим состояние.

Выполните
git status
Вы увидите:

Результат
$ git status
On branch main
nothing to commit, working tree clean
Рабочая директория чиста, можем продолжить работу.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book7.md)   [Следующая](./book9.md)