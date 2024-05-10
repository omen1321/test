##  22. Просмотр отличающихся веток

Цели

Научиться просматривать отличающиеся ветки в репозитории.
01 Просмотрите текущие ветки

Теперь у нас есть две расходящиеся ветки в репозитории. Используйте следующую команду log для просмотра веток и их расхождения.

Выполните
git log --all --graph
Результат
$ git log --all --graph
* ee16740 2023-11-28 | Added README (HEAD -> main) [Alexander Shvets]
| * 0ee0113 2023-11-28 | Renamed hello.html; moved style.css (style) [Alexander Shvets]
| * 903eb1d 2023-11-28 | Included stylesheet into hello.html [Alexander Shvets]
| * 555372e 2023-11-28 | Added css stylesheet [Alexander Shvets]
|/  
* 9288a33 2023-11-28 | Added copyright statement with email [Alexander Shvets]
* b7614c1 2023-11-28 | Added HTML header (tag: v1) [Alexander Shvets]
* 46afaff 2023-11-28 | Added standard HTML page tags (tag: v1-beta) [Alexander Shvets]
* 78433de 2023-11-28 | Added h1 tag [Alexander Shvets]
* 5836970 2023-11-28 | Initial commit [Alexander Shvets]
Опция --all гарантирует, что мы видим все ветки, так как по умолчанию в логе показывается только текущая ветка.

Опция --graph добавляет простое дерево коммитов, представленное в виде простых текстовых линий. Мы видим обе ветки (style и main) причём ветка main помечена как HEAD, что означает, что она является текущей. Общим предком для обеих веток является ветка, в которую был внесен коммит «Added copyright statement with email».
---

### [Содержание](./bookgit.md)
### [Предыдущая](./book22.md)   [Следующая](./book24.md)