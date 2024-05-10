##  25. Разрешение конфликтов

Цели

Научиться разрешать конфликты во время слияния.
01 Слияние main в ветку style

Давайте вернемся в ветку style и сольем в нее все последние изменения из ветки main.

Выполните
git switch style
git merge main
Результат
$ git switch style
Switched to branch 'style'
$ git merge main
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
Похоже, что у нас возник конфликт. Ничего удивительного! Посмотрим, что скажет по этому поводу Git:

Выполните
git status
Результат
$ git status
On branch style
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
Если открыть файл index.html, то можно увидеть:

Файл: index.html
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
<<<<<<< HEAD:index.html
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
=======
    <title>Hello World Page</title>
>>>>>>> main:hello.html
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>Let's learn Git together.</p>
  </body>
</html>
Часть между <<<<<<< >>>>>>> является конфликтом. Верхняя часть соответствует ветке style, которая является текущей веткой (или HEAD) репозитория. Нижняя часть соответствует изменениям из ветки main. Git не может решить, какие изменения применить, поэтому он просит вас разрешить конфликт вручную. Вы можете оставить изменения из ветки style или из main, либо объединить их любым удобным способом. Вы также можете внести в файл любые другие изменения.

Кстати, вы заметили, что наше второе изменение, тег <p>, не является частью конфликта? Это потому, что Git сумел автоматически объединить ее.

02 Отмена слияния

Прежде чем мы приступим к разрешению нашего конфликта, хочу заметить, что сразу бросаться к разрешению конфликта не всегда оптимально. Конфликт может быть вызван изменениями, о которых вы не знаете. Или же изменения слишком велики, чтобы разрешить конфликт сразу. По этой причине Git позволяет прервать слияние и вернуться к предыдущему состоянию. Для этого можно воспользоваться командой git merge --abort, как это было предложено командой status, которую мы выполнили ранее.

Выполните
git merge --abort
git status
Результат
$ git merge --abort
$ git status
On branch style
nothing to commit, working tree clean
03 Решение конфликта

После небольшой медитации мы готовы к разрешению конфликта. Давайте снова запустим объединение.

Выполните
git merge main
Чтобы разрешить конфликт, нужно отредактировать файл до состояния, которое нас устраивает, и затем закоммитить его как обычно. В нашем случае мы объединим изменения из обеих веток. Поэтому мы отредактируем файл до следующего состояния:

Файл: index.html
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
04 Закоммитьте разрешенный конфликт

Выполните
git add index.html
git commit -m "Resolved merge conflict"
git status
git log --all --graph
Результат
$ git add index.html
$ git commit -m "Resolved merge conflict"
[style 79ac6fa] Resolved merge conflict
Давайте посмотрим на текущее состояние нашего хранилища и убедимся, что все в порядке:

Выполните
git status
git log --all --graph
Результат
$ git status
On branch style
nothing to commit, working tree clean
$ git log --all --graph
*   79ac6fa 2023-11-28 | Resolved merge conflict (HEAD -> style) [Alexander Shvets]
|\  
| * 85c14e9 2023-11-28 | Added meta title (main) [Alexander Shvets]
* | a33deed 2023-11-28 | Merge branch 'main' into style [Alexander Shvets]
|\| 
| * ee16740 2023-11-28 | Added README [Alexander Shvets]
* | 0ee0113 2023-11-28 | Renamed hello.html; moved style.css [Alexander Shvets]
* | 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* | 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
|/  
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
05 Расширенные возможности слияния

Git не предоставляет никаких графических инструментов слияния, но будет с удовольствием работать с любыми сторонними инструментами слияния, которые вы хотите использовать (обсуждение таких инструментов на StackOverflow).

При работе с кодом в современной интегрированной среде разработки (IDE), такой как Visual Studio или IntelliJ IDEA, вы, скорее всего, будете использовать встроенный инструмент слияния. Например, вот как выглядит разрешение конфликтов в IntelliJ IDEA:

![emg](/assets/ide-merge-2x.png)
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book25.md)   [Следующая](./book27.md)