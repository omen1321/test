##  20. Перемещение файлов

Цели

Научиться перемещать файлы в пределах репозитория.
Я доволен нашими CSS-изменениями, но есть только один момент, который я хотел бы решить до того, как мы объединим наши изменения с main. Давайте переименуем файл hello.html в index.html. Также давайте перенесем наш файл стилей в специально отведенную директорию css.

01 Просмотр истории изменений в конкретном файле

Git позволяет просматривать историю изменений конкретного файла. Давайте посмотрим историю изменений файла hello.html перед его переименованием.

Выполните
git log hello.html
git log style.css
Результат
$ git log hello.html
903eb1d 2023-11-28 | Included stylesheet into hello.html (HEAD -> style) [Alexander Shvets]
9288a33 2023-11-28 | Added copyright statement with email (main) [Alexander Shvets]
b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
5836970 2023-11-28 | Initial commit [Alexander Shvets]
$ git log style.css
555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
02 Просмотр различий для конкретного файла

Возможность просмотра истории изменений для конкретного файла очень полезна. Она позволяет увидеть, что именно изменилось, а также кто и когда внес эти изменения. Кроме того, существует возможность увидеть изменения, связанные с конкретным коммитом. Я постоянно пользуюсь этим, чтобы разобраться, почему та или иная штука была реализована именно так в настоящей версии кода.

Команда show используется для просмотра изменений в конкретном коммите. Посмотрим изменения в файле hello.html в коммите, с тегом v1 (можно использовать любую ссылку на коммит, например, метку HEAD, хеш коммита, имя ветки или тега и т.д.).

Выполните
git show v1
Результат
$ git show v1
b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]

diff --git a/hello.html b/hello.html
index 6da0629..0d576c4 100644
--- a/hello.html
+++ b/hello.html
@@ -1,4 +1,6 @@
 <html>
+  <head>
+  </head>
   <body>
     <h1>Hello, World!</h1>
   </body>
03 Переименуйте файл hello.html

Как видите, очень удобно иметь возможность видеть историю изменений конкретного файла. Но когда вы переименовываете или перемещаете какой-либо файл, есть риск потерять историю этого файла, если вы выполните эту процедуру неправильно.

Давайте переименуем наш файл hello.html в index.html с помощью стандартной команды mv и посмотрим, что из этого получится.

Выполните
mv hello.html index.html
git status
Результат
$ mv hello.html index.html
$ git status
On branch style
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	deleted:    hello.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	index.html

no changes added to commit (use "git add" and/or "git commit -a")
Git воспринимает наше изменение так, будто файл был удален и создан заново. Это тревожный звоночек. Нам нужно сообщить Git, что мы именно переименовали файл, а не удалили его и сразу создали новый. В простейшем случае Git сам поймёт, что файл был переименован, как только мы добавим его в индекс:

Выполните
git add .
git status
Результат
$ git add .
$ git status
On branch style
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    hello.html -> index.html

Видите, файл указан как переименованный. Но это всего лишь Git пытается проявить смекалку. Это не всегда работает. Например, если вы переименовали, а также изменили кучу файлов, Git может оказаться не в состоянии понять, что именно было переименовано. В этом случае вы можете потерять информацию об истории файлов до их переименования, поскольку файлы будут восприняты как новые.

04 Переместите style.css безопасным способом

В большинстве операционных систем переименование и перемещение файлов — это одно и то же. Итак, давайте переместим наш файл style.css в директорию css, но на этот раз сделаем это безопасно с помощью команды git mv. Эта команда гарантирует, что перемещение будет записано в истории Git как перемещение.

Выполните
mkdir css
git mv style.css css/style.css
git status
Результат
$ mkdir css
$ git mv style.css css/style.css
$ git status
On branch style
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    style.css -> css/style.css
	renamed:    hello.html -> index.html

Давайте закоммитим наши изменения и проверим историю изменений в файле css/styles.css. Для просмотра истории файла до его перемещения нам потребуется добавить опцию --follow. Выполним оба варианта команды, чтобы понять разницу.

Выполните
git commit -m "Renamed hello.html; moved style.css"
git log css/style.css
git log --follow css/style.css
Результат
$ git commit -m "Renamed hello.html; moved style.css"
[style 0ee0113] Renamed hello.html; moved style.css
 2 files changed, 0 insertions(+), 0 deletions(-)
 rename style.css => css/style.css (100%)
 rename hello.html => index.html (100%)
$ git log css/style.css
0ee0113 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> style) [Alexander Shvets]
$ git log --follow css/style.css
0ee0113 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> style) [Alexander Shvets]
555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book20.md)   [Следующая](./book22.md)