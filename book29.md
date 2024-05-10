##  28. Перебазирование

Цели

Использовать команду rebase вместо команды merge.
Мы вернули ветку style к точке перед первым слиянием. При этом в ветке main есть два коммита, которых нет в ветке style: новый файл README и конфликтующее изменение в файле index.html. На этот раз мы перенесем эти изменения в ветку style с помощью команды rebase, а не merge.

01 Перебазируем ветку style на ветку main

Выполните
git switch style
git rebase main
git status
Результат
$ git switch style
Already on 'style'
$ git rebase main
Rebasing (1/3)
Rebasing (2/3)
Auto-merging hello.html
CONFLICT (content): Merge conflict in hello.html
error: could not apply 903eb1d... Included stylesheet into hello.html
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 903eb1d... Included stylesheet into hello.html
$ git status
interactive rebase in progress; onto 85c14e9
Last commands done (2 commands done):
   pick 555372e Added css stylesheet
   pick 903eb1d Included stylesheet into hello.html
Next command to do (1 remaining command):
   pick 0ee0113 Renamed hello.html; moved style.css
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'style' on '85c14e9'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
	both modified:   hello.html

no changes added to commit (use "git add" and/or "git commit -a")
Опять возник конфликт! Обратите внимание, что конфликт возник в файле hello.html, а не в файле index.html, как в прошлый раз. Это связано с тем, что rebase находился в процессе применения изменений style поверх ветки main. Файл hello.html в main еще не был переименован, поэтому он все еще имеет старое имя.

При слиянии возник бы «обратный» конфликт. При слиянии изменения ветки main были бы применены поверх ветки style. В ветке style файл переименован, поэтому конфликт возник бы в файле index.html.

Файл: hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
<<<<<<< HEAD
    <title>Hello World Page</title>
=======
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
>>>>>>> 903eb1d (Included stylesheet into hello.html)
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>Let's learn Git together.</p>
  </body>
</html>
02 Разрешение конфликта

Сам конфликт может быть разрешен тем же способом, что и предыдущий. Сначала мы изменим файл hello.html, чтобы он соответствовал нашим ожиданиям.

Файл: hello.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <title>Hello World Page</title>
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>Let's learn Git together.</p>
  </body>
</html>
Но после этого нам не нужно коммитить изменения. Мы можем просто добавить файл в индекс и продолжить процесс rebase. Вот почему я люблю rebase! Он позволяет мне устранять конфликты, не создавая кучу уродливых конфликтов слияния.

Для простоты мы можем добавить все изменения, используя ., что означает путь к текущей директории. Git интерпретирует это как «добавить все изменения из текущей директории и её поддиректорий».
Выполните
git add .
git rebase --continue
Здесь, скорее всего, Git снова откроет редактор, чтобы позволить нам изменить текст коммита. Мы можем оставить текст без изменений. После сохранения изменений Git завершит процесс rebase, и мы cможем выполнить следующие команды:

Выполните
git status
git log --all --graph
Результат
$ git add .
$ git rebase --continue
[detached HEAD 23149b5] Included stylesheet into hello.html
 1 file changed, 1 insertion(+)
Rebasing (3/3)

[KSuccessfully rebased and updated refs/heads/style.
$ git status
On branch style
nothing to commit, working tree clean
$ git log --all --graph
* 39a1e0f 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> style) [Alexander Shvets]
* 23149b5 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* b9e6de1 2023-11-28 | Added css stylesheet [Alexander Shvets]
* 85c14e9 2023-11-28 | Added meta title (main) [Alexander Shvets]
* ee16740 2023-11-28 | Added README [Alexander Shvets]
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
03 Слияние VS перебазирование

Конечный результат перебазирования очень похож на результат слияния. Ветка style в настоящее время содержит все свои изменения, а также все изменения ветки main. Однако, дерево коммитов значительно отличается. Дерево коммитов ветки style было переписано таким образом, что ветка main является частью истории коммитов. Это делает цепь коммитов линейной и гораздо более читабельной.

04 Когда использовать команду rebase, а когда команду merge?

Используйте команду rebase:

Когда вы получаете изменения из удаленного репозитория и хотите применить их к своей локальной ветке.
Если вы хотите, чтобы история коммитов была линейной и легко читаемой.
Не используйте команду rebase:

Если текущая ветка является публичной и общей. Переписывание таких веток будет мешать работе других членов команды.
Если важна точная история ветки коммитов (поскольку команда rebase переписывает историю коммитов).
Учитывая приведенные выше рекомендации, я предпочитаю использовать команду rebase для краткосрочных, локальных веток и команду merge для веток в публичном репозитории.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book28.md)   [Следующая](./book30.md)