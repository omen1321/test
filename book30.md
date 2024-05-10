##  29. Слияние в ветку main

Цели

Мы поддерживали соответствие ветки style с веткой main (с помощью rebase), теперь давайте сольем изменения style в ветку main.
01 Слейте style в main

Выполните
git switch main
git merge style
Результат
$ git switch main
Switched to branch 'main'
$ git merge style
Updating 85c14e9..39a1e0f
Fast-forward
 css/style.css            | 3 +++
 hello.html => index.html | 1 +
 2 files changed, 4 insertions(+)
 create mode 100644 css/style.css
 rename hello.html => index.html (73%)
Поскольку последний коммит в main предшествует последнему коммиту ветки style, Git может выполнить ускоренное слияние, просто переместив указатель ветки вперед, на тот же коммит, что и ветка style.

При ускоренном слиянии конфликты не возникают. Кроме того, при ускоренном слиянии не создается фиксация слияния.

02 Просмотрите логи

Выполните
git log --all --graph
Результат
$ git log --all --graph
* 39a1e0f 2023-11-28 | Renamed hello.html; moved style.css (HEAD -> main, style) [Alexander Shvets]
* 23149b5 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
* b9e6de1 2023-11-28 | Added css stylesheet [Alexander Shvets]
* 85c14e9 2023-11-28 | Added meta title [Alexander Shvets]
* ee16740 2023-11-28 | Added README [Alexander Shvets]
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
Теперь ветки style и main идентичны.
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book29.md)   [Следующая](./book31.md)