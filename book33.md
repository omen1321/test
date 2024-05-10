##  31. Просмотр клонированного репозитория

Цели

Узнать о ветках в удаленных репозиториях.
01 Посмотрите на клонированный репозиторий

Давайте взглянем на клонированный репозиторий.

Выполните
cd home
ls
Результат
$ cd home
$ ls
css
index.html
README
Вы увидите список всех файлов на верхнем уровне оригинального репозитория README, index.html и css).

02 Просмотрите историю репозитория

Выполните
git log --all
Результат
$ git log --all --graph
* 39a1e0f 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> main, origin/style, origin/main, origin/HEAD) [Alexander Shvets]
* 23149b5 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* b9e6de1 2023-11-28 | Added css stylesheet [Alexander Shvets]
* 85c14e9 2023-11-28 | Added meta title [Alexander Shvets]
* ee16740 2023-11-28 | Added README [Alexander Shvets]
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
Вы увидите список всех коммитов в новый репозиторий, и он должен совпадать с историей коммитов в оригинальном репозитории. Единственная разница должна быть в названиях веток.

03 Удаленные ветки

Вы увидите ветку main (HEAD) в списке истории. Вы также увидите ветки со странными именами (origin/main, origin/style и origin/HEAD). Мы поговорим о них чуть позже.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book32.md)   [Следующая](./book34.md)